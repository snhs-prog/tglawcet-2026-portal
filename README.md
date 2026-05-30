TG LAWCET 2026 Rank Estimator Portal
✅ Firebase is Already Configured!
Your Firebase project tglawcet-2026 is set up and ready to use.

🚀 How to Deploy (2 Steps)
Step 1: Set Firestore Security Rules

Go to Firebase Console: https://console.firebase.google.com/project/tglawcet-2026/firestore

Click "Rules" tab

Replace everything with this code and click "Publish":

javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /lawcet2026_entries/{doc} {
      // Anyone can read entries (for the live leaderboard)
      allow read: if true;
      // Only allow valid submissions
      allow create: if request.resource.data.score is int
                    && request.resource.data.score >= 0
                    && request.resource.data.score <= 120
                    && request.resource.data.name is string
                    && request.resource.data.name.size() >= 2
                    && request.resource.data.examType in ['3Y', '5Y', 'PG']
                    && request.resource.data.category is string;
    }
  }
}
Step 2: Deploy to GitHub Pages

Go to GitHub: https://github.com/new

Repository name: tglawcet-2026-portal

Public → Click "Create repository"

Click "uploading an existing file"

Drag tglawcet-rank-portal.html into the upload box

Commit: Initial portal upload

Go to Settings → Pages (left sidebar)

Under "Build and deployment":

Source: Deploy from a branch

Branch: main (or master)

Folder: / (root)

Click "Save"

Wait 1–2 minutes → Your site goes live at:

text
https://yourusername.github.io/tglawcet-2026-portal/
📊 Your Firebase Project Details
Setting	Value
Project ID	tglawcet-2026
Firestore Collection	lawcet2026_entries
Free Tier	Spark (Free)
Reads/Day	50,000 free
Writes/Day	20,00
