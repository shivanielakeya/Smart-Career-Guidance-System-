# Smart-Career-Guidance-System-
A full stack web application to help students take career decisions based on their interest , aptitude, skills and preference. The system offers personalized career recommendations based on interactive assessments and intuitive user interface.

## Overview

This system helps students discover their ideal career path through:
- **Personal Profile Management**: Capture student details, school information, and location
- **Education Records**: Support for both 10th and 12th standard education data
- **Aptitude Assessment**: Comprehensive aptitude testing with multiple categories
- **Interest Assessment**: Career interest exploration across 8+ categories
- **Career Recommendations**: AI-driven recommendations based on assessments
- **College Recommendations**: Curated college suggestions with cutoff scores
- **Interactive Dashboard**: Real-time progress tracking with data visualizations

## Project Structure

```
career-guidance-system-combined/
│
├── frontend/
│   ├── src/
│   │   ├── components/          # Reusable React components
│   │   ├── pages/               # Page components (Home, Dashboard, Assessment, etc.)
│   │   ├── services/            # API client services
│   │   ├── hooks/               # Custom React hooks (useAuth)
│   │   ├── context/             # Context providers (AuthContext)
│   │   ├── routes/              # Routing configuration
│   │   ├── App.jsx              # Main App component
│   │   ├── main.jsx             # React entry point
│   │   └── index.css            # Global styles (Tailwind)
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   ├── .env.example
│   └── index.html
│
├── backend/
│   ├── app/
│   │   ├── api/                 # API route modules (auth, students, education, etc.)
│   │   ├── db/
│   │   │   ├── models/          # SQLAlchemy ORM models
│   │   │   ├── session.py       # Database session management
│   │   │   ├── base.py          # Base model configuration
│   │   │   └── seed.py          # Database seeding
│   │   ├── schemas/             # Pydantic request/response schemas
│   │   ├── services/            # Business logic (auth_service)
│   │   ├── core/
│   │   │   ├── config.py        # Configuration management
│   │   │   ├── security.py      # JWT and password utilities
│   │   │   └── dependencies.py  # FastAPI dependencies
│   │   ├── main.py              # FastAPI app initialization
│   │   └── __init__.py
│   ├── requirements.txt         # Python dependencies
│   ├── .env                     # Environment variables (backend)
│   ├── .env.example             # Environment template
│   └── career_guidance_dev.db   # SQLite database
│
├── Makefile                     # Convenience commands
├── README.md                    # This file
├── MERGE_REPORT.md              # Detailed merge documentation
└── .gitignore

```

## Getting Started

### Prerequisites

- **Node.js** (v18+) and npm for frontend
- **Python** (3.9+) for backend
- **Git** for version control
- A terminal/command prompt

### Frontend Setup

1. **Navigate to frontend directory**:
   ```bash
   cd frontend
   ```

2. **Install dependencies**:
   ```bash
   npm install
   ```

3. **Create environment file** (`.env`):
   ```bash
   cp .env.example .env
   ```

   Edit `.env` and set:
   ```
   VITE_API_BASE_URL=http://127.0.0.1:8000
   ```

4. **Start development server**:
   ```bash
   npm run dev
   ```

   Frontend will be available at `http://localhost:5173`

### Backend Setup

1. **Navigate to backend directory**:
   ```bash
   cd backend
   ```

2. **Create Python virtual environment** (recommended):
   ```bash
   python -m venv venv
   
   # Activate virtual environment
   # On Linux/Mac:
   source venv/bin/activate
   
   # On Windows:
   venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

4. **Setup environment file** (`.env`):
   ```bash
   cp .env.example .env
   ```

   Default `.env` should contain:
   ```
   DATABASE_URL=sqlite:///./career_guidance_dev.db
   SECRET_KEY=your-secret-key-here-change-in-production
   ACCESS_TOKEN_EXPIRE_MINUTES=30
   CORS_ORIGINS=["http://localhost:4173", "http://localhost:5173", "http://localhost:3000", "http://127.0.0.1:4173", "http://127.0.0.1:5173", "http://127.0.0.1:3000"]
   ```

5. **Initialize database** (first time only):
   ```bash
   python -c "from app.db.session import engine; from app.db.base import Base; Base.metadata.create_all(bind=engine)"
   ```

6. **Seed database with sample data** (optional):
   ```bash
   python -c "from app.db.seed import seed_database; seed_database()"
   ```

7. **Start backend server**:
   ```bash
   uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
   ```

   Backend will be available at `http://127.0.0.1:8000`
   API documentation: `http://127.0.0.1:8000/docs`

## Required Dependencies

### Frontend
- **React 18.3.1**: UI library
- **React Router 6.15**: Client-side routing
- **Vite 5.4.1**: Development build tool
- **Tailwind CSS 3.4.4**: Utility-first CSS framework
- **Axios 1.6.5**: HTTP client
- **Recharts 2.8.0**: Data visualization (charts, graphs)
- **Lucide React 0.530.0**: Icon library

### Backend
- **FastAPI 0.111.1**: Modern web framework
- **Uvicorn 0.24.0**: ASGI server
- **SQLAlchemy 2.0.22**: ORM for database
- **Pydantic 2.10.16**: Data validation
- **Python-Jose 3.1.0**: JWT authentication
- **Passlib[bcrypt] 1.7.4**: Password hashing
- **Python-dotenv 1.0.1**: Environment variable management

## Environment Variables

### Frontend (.env)
```
VITE_API_BASE_URL=http://127.0.0.1:8000
```

### Backend (.env)
```
DATABASE_URL=sqlite:///./career_guidance_dev.db
SECRET_KEY=your-very-secure-key-change-for-production
ACCESS_TOKEN_EXPIRE_MINUTES=30
CORS_ORIGINS=["http://localhost:4173", "http://localhost:5173", "http://localhost:3000", "http://127.0.0.1:4173", "http://127.0.0.1:5173", "http://127.0.0.1:3000"]
DATABASE_ECHO=False
```

**Production Notes:**
- Change `SECRET_KEY` to a strong, unique value
- Use PostgreSQL (`postgresql://user:password@localhost/dbname`) for production
- Add your frontend production URL to `CORS_ORIGINS`

## Development URLs

| Component | URL | Purpose |
|-----------|-----|---------|
| Frontend | `http://localhost:5173` | React application |
| Backend | `http://127.0.0.1:8000` | API server |
| API Docs | `http://127.0.0.1:8000/docs` | Swagger UI documentation |
| ReDoc | `http://127.0.0.1:8000/redoc` | Alternative API documentation |

## Complete User Flow

The system follows this linear assessment flow:

1. **Homepage** (`/`)
   - Project overview
   - Browse careers without login
   - Call-to-action to start assessment

2. **Get Started** (`/get-started`)
   - Introduction to the assessment process
   - Button to navigate to register

3. **Register** (`/register`)
   - Create new student account
   - Email and password authentication
   - Automatic login after registration

4. **Login** (`/login`)
   - Existing student login
   - JWT token generation
   - Redirect to dashboard

5. **Personal Details** (`/personal-details`)
   - Student name, email, phone
   - School and location information
   - Save to database

6. **Education Details** (`/education-details`)
   - Support for BOTH 10th and 12th records
   - Can be filled in any order
   - Board, stream, marks, percentage
   - Multiple submissions create/update separate records

7. **Aptitude Assessment** (`/aptitude-assessment`)
   - 20+ questions across categories
   - 30-minute timer (auto-submit on timeout)
   - Question palette for quick navigation
   - Mark for review feature
   - Score calculation by category

8. **Interest Assessment** (`/interest-assessment`)
   - Interest inventory across 8+ categories
   - Score calculation for each interest
   - Visual results display

9. **Review Assessment** (`/review`)
   - Summary of all assessment results
   - Personal profile review
   - Education summary
   - Aptitude results with breakdown
   - Interest distribution
   - Proceed to dashboard for recommendations

10. **Dashboard** (`/dashboard`)
    - Profile completion percentage
    - 10th and 12th marks display
    - Aptitude score with radar chart visualization
    - Interest distribution with pie chart
    - Top 3 career recommendations with match scores
    - Recommended courses
    - Recommended colleges
    - Links to update information

11. **College Recommendations** (`/colleges`)
    - Browse and filter colleges
    - Match percentage with student profile
    - Cutoff scores and requirements
    - Course offerings

12. **Logout**
    - Session termination
    - Redirect to homepage

## API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - Register new student
- `POST /api/auth/login` - Login and get JWT token
- `POST /api/auth/logout` - Logout (clears session)

### Student Endpoints
- `GET /api/students/profile` - Get student profile
- `PUT /api/students/profile` - Update student profile

### Education Endpoints
- `GET /api/education/records` - Get all education records
- `POST /api/education/records` - Create education record
- `PUT /api/education/records/{id}` - Update education record
- `DELETE /api/education/records/{id}` - Delete education record

### Aptitude Endpoints
- `GET /api/aptitude/questions` - Get all aptitude questions
- `POST /api/aptitude/submit` - Submit aptitude answers
- `GET /api/aptitude/result` - Get aptitude result and scores

### Interest Endpoints
- `GET /api/interest/questions` - Get all interest questions
- `POST /api/interest/submit` - Submit interest answers
- `GET /api/interest/result` - Get interest result and scores

### Recommendation Endpoints
- `GET /api/recommendations/careers` - Get career recommendations
- `GET /api/recommendations/colleges` - Get college recommendations
- `GET /api/recommendations/courses` - Get course recommendations

### Health Check
- `GET /api/health/check` - API health status

**Full API documentation available at:** `http://127.0.0.1:8000/docs`

## Database Schema

### Key Models
- **User** - Authentication and login
- **StudentProfile** - Personal and school information
- **EducationRecord** - 10th and 12th academic records (multiple records supported)
- **AptitudeQuestion** - Aptitude test questions
- **AptitudeResponse** - Student's aptitude answers
- **AptitudeResult** - Calculated aptitude score and category breakdown
- **InterestQuestion** - Career interest questions
- **InterestOption** - Multiple choice options for interest questions
- **InterestResponse** - Student's interest answers
- **Career** - Career options (seeded data)
- **College** - College options with cutoffs (seeded data)

## Testing the Application

### Manual Testing Checklist

1. **Authentication Flow**
   - ✅ Register with valid credentials
   - ✅ Login with correct credentials
   - ✅ Cannot login with wrong password
   - ✅ Cannot access protected routes without login
   - ✅ Logout clears session

2. **Personal Details**
   - ✅ Fill and save personal information
   - ✅ Update personal information
   - ✅ Validation on required fields

3. **Education Details**
   - ✅ Add 10th education record
   - ✅ Add 12th education record
   - ✅ Both records persist independently
   - ✅ Can update existing records
   - ✅ Percentage auto-calculates correctly

4. **Aptitude Assessment**
   - ✅ Questions load from API
   - ✅ Timer counts down
   - ✅ Can navigate between questions
   - ✅ Mark for review works
   - ✅ Submit with unanswered questions shows confirmation
   - ✅ Score calculated and saved
   - ✅ Redirects to interest assessment after submit

5. **Interest Assessment**
   - ✅ Questions load
   - ✅ Options display correctly
   - ✅ Answers save
   - ✅ Results show with percentages

6. **Dashboard**
   - ✅ Profile completion percentage displays correctly
   - ✅ 10th and 12th marks show separately
   - ✅ Aptitude score and radar chart display
   - ✅ Interest distribution pie chart displays
   - ✅ Career recommendations with match scores show
   - ✅ Course and college recommendations display

7. **Responsive Design**
   - ✅ Desktop (1024px+): Full layout
   - ✅ Tablet (768px-1023px): Adjusted grid
   - ✅ Mobile (< 768px): Single column stack
   - ✅ All cards and forms are readable
   - ✅ Navigation works on all devices

### Browser Console Check
- ✅ No JavaScript errors
- ✅ No CORS errors
- ✅ All API calls complete successfully

### Backend API Check
```bash
curl http://127.0.0.1:8000/api/health/check
# Should return: {"status": "healthy"}
```

## Responsive Design

The application is fully responsive with Tailwind CSS breakpoints:

- **Mobile**: < 768px (single column, stacked layout)
- **Tablet**: 768px - 1023px (2-column grid)
- **Desktop**: 1024px+ (full multi-column layout)

All components maintain the Figma design system across all screen sizes.

## Known Limitations

1. **Database**: Currently uses SQLite for development. Migrate to PostgreSQL for production.
2. **Career Data**: Limited to seed data. Can expand with more careers and colleges.
3. **ML Recommendations**: Uses rule-based scoring. ML models can be added in Phase 3.
4. **Authentication**: JWT-based. Consider adding OAuth2 or two-factor authentication.
5. **File Uploads**: Profile picture uploads not yet implemented.
6. **Email Notifications**: Email verification and password reset not yet implemented.
7. **TNEA Integration**: Large college dataset integration pending.

## Future Phases

### Phase 3 (Planned)
- [ ] Google Apps Script integration for result sheets
- [ ] PDF report generation
- [ ] AI-powered career chatbot
- [ ] Machine learning recommendation engine
- [ ] Large TNEA college database
- [ ] Advanced analytics

### Phase 4 (Planned)
- [ ] Multi-language support
- [ ] Mobile app (React Native)
- [ ] Parent/Guardian dashboard
- [ ] Advanced progress tracking
- [ ] Peer comparison analytics
- [ ] Scheduled notifications

## Troubleshooting

### Frontend Issues

**Problem: "Cannot GET /"**
- Make sure frontend dev server is running: `npm run dev` in frontend directory
- Check that you're accessing `http://localhost:5173` (not 5173 is the default, check terminal output)

**Problem: "API connection refused"**
- Verify backend is running: `uvicorn app.main:app --reload`
- Check `VITE_API_BASE_URL` in `.env` matches backend URL
- Ensure CORS is properly configured in backend

**Problem: "Module not found" errors**
- Run `npm install` again
- Delete `node_modules` and `package-lock.json`, then reinstall
- Clear npm cache: `npm cache clean --force`

### Backend Issues

**Problem: "ImportError: No module named 'app'"**
- Make sure you're running from the backend directory
- Virtual environment not activated? Run `source venv/bin/activate` (Linux/Mac) or `venv\Scripts\activate` (Windows)

**Problem: "Database locked" error**
- Close any other processes using the database
- Delete `career_guidance_dev.db` and restart (WARNING: Clears all data)
- Try using PostgreSQL instead for development

**Problem: "CORS error" in browser**
- Check `CORS_ORIGINS` in backend `.env`
- Make sure frontend URL matches exactly
- Restart backend after changing `.env`

**Problem: "Port already in use"**
- Frontend: `npm run dev -- --port 3000` (for port 3000)
- Backend: `uvicorn app.main:app --port 8001` (for port 8001)

## Performance Optimization

### Frontend
- Lazy load routes using React Router
- Memoize expensive components
- Use recharts' responsive containers
- Compress images and use appropriate formats

### Backend
- Database query optimization with eager loading
- API response caching where appropriate
- Batch operations for bulk inserts
- Consider adding Redis cache layer

## Security Considerations

1. **Authentication**: JWT tokens stored in httpOnly cookies (recommended)
2. **Password**: Hashed with bcrypt
3. **CORS**: Configured to allow only frontend origin
4. **Environment**: Sensitive keys in `.env` (never commit)
5. **SQL Injection**: Protected by SQLAlchemy ORM
6. **Rate Limiting**: Consider adding for production
7. **HTTPS**: Required for production deployment

## Deployment

### Frontend Deployment (Vercel, Netlify)
```bash
npm run build
# Deploy 'dist' folder
```

### Backend Deployment (Heroku, Railway, AWS)
```bash
# Use Gunicorn for production:
gunicorn -w 4 -k uvicorn.workers.UvicornWorker app.main:app
```

## Support & Documentation

- **API Documentation**: http://127.0.0.1:8000/docs (Swagger UI)
- **Report Issues**: Create an issue in the project repository
- **Database Models**: See `backend/app/db/models/`
- **Services**: See `frontend/src/services/`

## License

This project is developed for educational purposes.

## Contributors

**Phase 1 (UI/Design)**: Figma-based design system  
**Phase 2 (Backend/API)**: Complete FastAPI backend  
**Combined (Integration)**: Merged and tested system

---

**Last Updated**: August 2026  
**Version**: 1.0.0 (Combined)
