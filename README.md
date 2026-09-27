# Chapter 3: Develop Mobile Hosting Solution with Cloud

## 📋 Overview

This lab guides you through building and deploying a modern web application using **AWS Amplify**. You will create a React application from scratch, host its source code on GitHub, and leverage AWS Amplify to automatically build, deploy, and host your application on a globally available Content Delivery Network (CDN). You will also demonstrate continuous deployment by making code changes and watching them automatically go live.

**AWS Amplify** is a set of tools and services that helps front-end web and mobile developers build scalable full-stack applications powered by AWS. With Amplify, you can configure app backends, connect your app in minutes, deploy static web apps in a few clicks, and easily manage app content outside the AWS console.

Amplify supports popular web frameworks including JavaScript, React, Angular, Vue, Next.js, and mobile platforms including Android, iOS, React Native, Ionic, and Flutter.

---

## 🎯 Lab Objectives

By the end of this lab, you will have successfully:

- ✅ Created a React application using `create-react-app`
- ✅ Initialized a GitHub repository and pushed your code to it
- ✅ Deployed your application with AWS Amplify
- ✅ Implemented code changes and automatically redeployed your app

---

## 👤 Grouping Method

This is an **individual exercise**. Each student should complete all tasks independently.

---

## 🏗️ Lab Environment

At the end of this lab, your architecture will consist of:

- A **React application** running locally during development
- A **GitHub repository** storing your application source code
- **AWS Amplify** connected to your GitHub repository for continuous integration and continuous deployment (CI/CD)
- A globally available **CDN endpoint** (`https://<unique-id>.amplifyapp.com`) hosting your deployed application

---

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed on your local machine:

| Requirement | Minimum Version | Notes |
|---|---|---|
| **Node.js** | v16.x or later | Required to run React and npm |
| **npm** | v6.x or later | Comes bundled with Node.js |
| **Git** | v2.37.2 or later | Version control system |
| **GitHub Desktop** | Latest | Optional GUI alternative for Git commands |
| **GitHub Account** | — | Free account at [github.com](https://github.com) |
| **AWS Account** | — | Access to the AWS Management Console |

> **💡 Tip:** You can verify your installed versions by running `node -v`, `npm -v`, and `git --version` in your terminal or command prompt.

---

## 📝 Task 1: Create a New React Application

In this task, you will scaffold a new React application using the `create-react-app` utility.

### Step 1.1 — Open your terminal

- **Windows:** Open **Command Prompt** (`cmd`) or **PowerShell**
- **macOS / Linux:** Open **Terminal**

### Step 1.2 — Create the React app

Run the following command. This uses `npx` to download and execute the `create-react-app` package, which scaffolds a new React project named `amplifyapp`.

```bash
npx create-react-app amplifyapp
```

> ⏳ This may take a few minutes as it downloads and installs all dependencies.

### Step 1.3 — Navigate into the project directory

```bash
cd amplifyapp
```

### Step 1.4 — Start the development server

```bash
npm start
```

### Step 1.5 — Verify the app is running

After a successful compilation, you should see output similar to:

```
Compiled successfully!

You can now view amplifyapp in the browser.

  Local:            http://localhost:3000
  On Your Network:  http://192.168.x.x:3000
```

A web browser window should automatically open at `http://localhost:3000` displaying the default React welcome page with a spinning logo.

> **🛑 Important:** Once you have confirmed the app runs successfully, stop the development server by pressing `Ctrl + C` in your terminal. You will not need it running for the remaining tasks.

---

## 📝 Task 2: Initialize a GitHub Repository

In this task, you will create a new public repository on GitHub and push your local React application code to it.

### Step 2.1 — Create a new repository on GitHub

1. Open your browser and navigate to [GitHub](https://github.com).
2. Sign in to your account. If you do not have an account, [sign up here](https://github.com/signup).
3. Click the **+** icon in the top-right corner and select **New repository**, or visit [this direct link](https://github.com/new).
4. Configure the repository with the following settings:

| Setting | Value |
|---|---|
| **Repository name** | `amplifyapp` |
| **Description** | `This is my first Amplify app` |
| **Visibility** | **Public** |

5. **Do NOT** initialize the repository with a README, `.gitignore`, or license. Leave those options unchecked.
6. Click **Create repository**.

> ✅ Your empty GitHub repository is now ready. Keep this page open — you will need the repository URL.

### Step 2.2 — Initialize Git locally and push your code

You have two options: use the **command line** or **GitHub Desktop**. The command-line method is detailed below.

#### Using the Command Line

1. Open your terminal or Command Prompt.
2. Navigate to your project directory:

```bash
cd amplifyapp
```

3. Verify you are in the correct directory:

```bash
dir /w      # Windows
ls          # macOS / Linux
```

You should see files like `package.json`, `src/`, `public/`, `node_modules/`, etc.

4. Run the following commands **one by one**. Replace `{your-username}` with your actual GitHub username:

```bash
# Create a README file
echo "# amplifyapp" >> README.md

# Initialize a new Git repository
git init

# Stage the README file
git add README.md

# Create your first commit
git commit -m "first commit"

# Rename the default branch to 'main'
git branch -M main

# Link your local repository to the remote GitHub repository
git remote add origin https://github.com/{your-username}/amplifyapp.git

# Push your code to GitHub
git push -u origin main
```

> **⚠️ Note:** If you are prompted to authenticate, a browser window will pop up asking you to **Sign in with your browser** and **Authorize Git Credential Manager**. Complete the authorization to proceed.

#### Using GitHub Desktop (Alternative)

If you prefer a graphical interface, you can follow the official guide on cloning and pushing with GitHub Desktop:
🔗 [GitHub Desktop Tutorial Video](https://www.youtube.com/watch?v=xuq73UJrbwg&t=29s)

### Step 2.3 — Verify the push

1. Return to your GitHub repository page in your browser.
2. Refresh the page.
3. You should see your `README.md` file and the initial commit displayed.

> ✅ **Checkpoint:** Your code is now safely stored on GitHub.

---

## 📝 Task 3: Deploy Your Application with AWS Amplify

In this task, you will connect your GitHub repository to the AWS Amplify service. Amplify will automatically build your React application and deploy it to a global CDN.

### Step 3.1 — Open the AWS Amplify Console

1. Open a **new browser window** and sign in to the [AWS Management Console](https://console.aws.amazon.com/).
2. In the top search bar, type **Amplify** and select it, or navigate via **Services → Amplify**.

### Step 3.2 — Start the hosting setup

1. On the Amplify landing page, locate the **Get Started** section under **Deliver**.
2. Click **Get started**.

### Step 3.3 — Connect your GitHub repository

1. Select **GitHub** as your repository service provider.
2. Click **Continue**.
3. You will be prompted to authenticate with GitHub. Follow the on-screen instructions to authorize AWS Amplify to access your GitHub repositories.
4. Once authenticated, you will return to the Amplify console.
5. From the dropdown menus, select:
   - **Repository:** `amplifyapp`
   - **Branch:** `main`
6. Click **Next**.

### Step 3.4 — Review build settings

1. Amplify will auto-detect your React application and generate a default build configuration (`amplify.yml`).
2. Review the build settings. The defaults should be correct for a standard React app.
3. Click **Next** to accept the defaults.

### Step 3.5 — Review and deploy

1. Review the final summary of your deployment configuration.
2. Click **Save and deploy**.

### Step 3.6 — Monitor the build and deployment

1. AWS Amplify will now begin building your source code. You will see real-time build logs in the console.
2. The build process typically includes:
   - **Provision** — Setting up the build environment
   - **Build** — Running `npm install` and `npm run build`
   - **Deploy** — Uploading the built files to the CDN
   - **Verify** — Confirming the deployment
3. Wait for all phases to show a ✅ green checkmark.

### Step 3.7 — View your live application

1. Once the build completes, Amplify will display a **domain URL** in the format:
   ```
   https://<unique-id>.amplifyapp.com
   ```
2. Click the **thumbnail** or the **domain URL** to open your live web application.
3. You should see the default React welcome page — now hosted on AWS!

> ✅ **Checkpoint:** Your application is live on a globally available CDN.

---

## 📝 Task 4: Automatically Deploy Code Changes

One of the most powerful features of AWS Amplify is **continuous deployment**. Any change you push to your connected branch will automatically trigger a new build and deployment. In this task, you will modify your app and watch it update live.

### Step 4.1 — Modify the application code

1. Open your file explorer and navigate to your project directory:
   ```
   C:\Users\<your-username>\amplifyapp\src
   ```
   *(Adjust the path for macOS/Linux accordingly)*

2. Open `App.js` in any text editor (e.g., **Notepad**, **VS Code**, **Sublime Text**).

3. Replace the entire contents of `App.js` with the following code:

```jsx
import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      <header className="App-header">
        <img src={logo} className="App-logo" alt="logo" />
        <h1>Hello from V2</h1>
      </header>
    </div>
  );
}

export default App;
```

4. **Save** the file.

> **🔍 What changed?** The original React boilerplate contained multiple paragraphs of text and a link. We replaced all of that with a single `<h1>Hello from V2</h1>` heading to make the visual change obvious.

### Step 4.2 — Commit and push the changes

1. Open your terminal or Command Prompt.
2. Make sure you are in the `amplifyapp` directory:

```bash
cd amplifyapp
```

3. Stage all changes, commit, and push:

```bash
# Stage all modified files
git add .

# Commit the changes with a descriptive message
git commit -m "changes for v2"

# Push to the main branch on GitHub
git push origin main
```

> **⚠️ Note:** The lab manual references `git push origin master`. If your default branch is named `main` (as set up in Task 2), use `main`. If your branch is still named `master`, use `master` instead.

### Step 4.3 — Watch the automatic deployment

1. Return to the **AWS Amplify console** in your browser.
2. You should see a **new build** has been automatically triggered.
3. Monitor the build progress through the same phases: **Provision → Build → Deploy → Verify**.
4. Wait for the build to complete.

### Step 4.4 — Verify the updated application

1. Once the new build shows ✅ success, click the **thumbnail** or **domain URL**.
2. Your live application should now display:

   > **Hello from V2**

> ✅ **Checkpoint:** You have successfully demonstrated continuous deployment. Code changes pushed to GitHub are automatically built and deployed by AWS Amplify.

---

## 📝 Task 5: Clean Up Your Environment

After completing the lab, it is important to clean up your cloud resources to avoid any unexpected charges.

### Step 5.1 — Delete the Amplify app

1. In the **AWS Amplify console**, select your `amplifyapp` application.
2. Click **Actions** → **Delete app**.
3. Confirm the deletion when prompted.

> ⚠️ This will remove the hosting deployment and CDN distribution. Your GitHub repository will **not** be affected.

### Step 5.2 — Delete the GitHub repository *(optional)*

If you no longer need the repository:

1. Go to your repository on GitHub.
2. Click **Settings** → scroll down to the **Danger Zone** section.
3. Click **Delete this repository**.
4. Follow the confirmation prompts.

### Step 5.3 — Remove local files *(optional)*

You can delete the `amplifyapp` folder from your local machine if you no longer need the project files.

---

## ✅ Result Verification

You have successfully completed this lab if you can confirm all of the following:

| # | Objective | Status |
|---|---|---|
| 1 | Created a React application using `npx create-react-app` | ✅ |
| 2 | Initialized a GitHub repository and pushed your source code | ✅ |
| 3 | Deployed your app with AWS Amplify to a live CDN URL | ✅ |
| 4 | Implemented code changes and automatically redeployed your app | ✅ |

---

## 📌 Additional Notes

- **No additional tasks** are required for this chapter.
- AWS Amplify offers many advanced features beyond this lab, including backend authentication with **Amazon Cognito**, serverless APIs with **AWS AppSync**, and storage with **Amazon S3**. Explore these in future modules.
- If you encounter build failures, check the **Build logs** in the Amplify console for detailed error messages.

---

*End of Chapter 3 — Develop Mobile Hosting Solution with Cloud*
