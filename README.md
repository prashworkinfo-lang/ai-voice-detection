# AI Voice Detection System

A web-based AI voice detection system that analyzes audio files to determine whether they are AI-generated or human voices. Built with Flask and featuring a modern dark-themed interface.

## Live preview

https://aivoicedetection-t1hm.onrender.com/

## Features

- 🎤 Multiple audio input methods (file upload, URL, base64)
- 🔒 API key authentication
- 🎨 Modern dark UI with responsive design
- 📊 Confidence score and detailed analysis
- 🚀 Easy deployment on Render, Heroku, or Railway

## Demo

![AI Voice Detection Interface](https://via.placeholder.com/800x400?text=AI+Voice+Detection+Interface)

## Tech Stack

- **Backend:** Flask (Python)
- **Frontend:** HTML, CSS, JavaScript
- **Deployment:** Gunicorn WSGI server

## Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Local Setup

1. Clone the repository:
```bash
git clone <your-repo-url>
cd guvihackathon
```

2. Create a virtual environment:
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run the application:
```bash
python app.py
```

5. Open your browser and navigate to:
```
http://localhost:5000
```

## API Documentation

### Authentication

All API requests require authentication using an API key. Include the key in the request header:

```
Authorization: your-secret-api-key-12345
```
or
```
X-API-Key: your-secret-api-key-12345
```

**Note:** Change the default API key in `app.py` before deploying to production.

### Endpoint: `/detect`

**Method:** POST

**Request Body:**

Option 1 - Audio URL:
```json
{
  "audio_url": "https://example.com/audio.mp3"
}
```

Option 2 - Base64 Encoded Audio:
```json
{
  "audio_base64": "base64_encoded_audio_data_here"
}
```

**Response:**

```json
{
  "classification": "AI-Generated",
  "confidence_score": 85.5,
  "explanation": "Audio exhibits synthetic patterns in frequency distribution typical of AI-generated speech."
}
```

**Status Codes:**
- `200` - Success
- `400` - Bad Request (missing or invalid parameters)
- `401` - Unauthorized (invalid API key)
- `500` - Server Error

### Example cURL Request

```bash
curl -X POST https://your-app.onrender.com/detect \
  -H "Authorization: your-secret-api-key-12345" \
  -H "Content-Type: application/json" \
  -d '{"audio_url": "https://example.com/sample.mp3"}'
```

## Deployment

### Deploy on Render

1. Push your code to GitHub
2. Go to [Render Dashboard](https://render.com)
3. Click "New +" → "Web Service"
4. Connect your GitHub repository
5. Configure:
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `gunicorn app:app`
6. Click "Create Web Service"

### Deploy on Heroku

1. Install Heroku CLI
2. Login and create app:
```bash
heroku login
heroku create your-app-name
```

3. Deploy:
```bash
git push heroku main
```

### Deploy on Railway

1. Go to [Railway](https://railway.app)
2. Click "New Project" → "Deploy from GitHub"
3. Select your repository
4. Railway will auto-detect and deploy

## Environment Variables

For production deployment, set these environment variables:

- `API_KEY` - Your custom API key (default: `your-secret-api-key-12345`)
- `PORT` - Port number (automatically set by hosting platforms)

## Security Notes

⚠️ **Important for Production:**

1. **Change the default API key** in `app.py` or use environment variables
2. **Remove or secure the Gemini API key** if not in use
3. Consider implementing rate limiting
4. Use HTTPS in production
5. Implement proper logging and monitoring

## Project Structure

```
guvihackathon/
├── app.py              # Flask application
├── index.html          # Frontend interface
├── requirements.txt    # Python dependencies
├── render.yaml         # Render deployment config
├── .gitignore         # Git ignore rules
└── README.md          # Documentation
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is open source and available under the [MIT License](LICENSE).

## Acknowledgments

- Built for Guvi Hackathon
- Made with ❤️ by Prashant

## Support

For issues, questions, or suggestions, please open an issue on GitHub.

---

**Note:** This is a demonstration project. The AI detection algorithm uses a simplified approach for demo purposes. For production use, integrate with actual AI voice detection models or services.
