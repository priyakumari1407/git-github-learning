# Git & GitHub Basics

## 1. What is Git?

Git is a **Distributed Version Control System (DVCS)** used to track changes in files and source code.

Git helps developers:

* Track changes in code
* Save different versions of a project
* See what changed
* Restore previous versions
* Work on different features using branches
* Collaborate with other developers
* Maintain a history of the project

### Simple Example

Without Git:

```text
project-final
project-final-new
project-final-new2
project-final-latest
project-final-latest-fixed
```

With Git:

```text
Commit 1 → Commit 2 → Commit 3 → Commit 4
```

Git keeps the history of these changes.

---

## 2. What is GitHub?

GitHub is a platform that hosts Git repositories online.

Git and GitHub are different.

| Git                                            | GitHub                                        |
| ---------------------------------------------- | --------------------------------------------- |
| Version control system                         | Git repository hosting platform               |
| Runs locally on your computer                  | Primarily cloud-based                         |
| Tracks changes                                 | Stores and shares repositories                |
| Uses commands like `commit`, `branch`, `merge` | Provides Pull Requests, Issues, Actions, etc. |
| Can work without internet                      | Internet is needed for remote operations      |

### Simple Analogy

```text
Git = Tool that tracks your project changes

GitHub = Online platform where you can store,
         share and collaborate on Git repositories
```

---

# 3. What is Version Control?

Version control means **tracking and managing changes to files over time**.

For example:

```text
Version 1 → Login page
Version 2 → Login + Signup
Version 3 → Login + Signup + Dashboard
Version 4 → Bug fixes
```

Git stores these versions through **commits**.

---

# 4. What is a Repository?

A repository, or **repo**, is a project that Git is tracking.

Example:

```text
my-project/
│
├── src/
├── package.json
├── README.md
└── .git/
```

The `.git` folder contains Git's internal information, such as:

* Commit history
* Branch information
* Git objects
* References
* Repository configuration

### Important

Do not manually modify or delete the `.git` folder.

---

# 5. Local Repository vs Remote Repository

### Local Repository

The repository on your own computer.

```text
Your Computer
      ↓
Local Git Repository
```

### Remote Repository

A repository hosted somewhere else, such as GitHub.

```text
Your Computer
      ↓
   Git / Network
      ↓
    GitHub
```

Example:

```text
Local Repository
       ↕
     GitHub
```

---

# 6. Installing Git

Check whether Git is installed:

```bash
git --version
```

Example:

```text
git version 2.x.x
```

If a version is displayed, Git is installed.

---

# 7. Configure Git

Git needs to know the identity associated with your commits.

Set your name:

```bash
git config --global user.name "Your Name"
```

Set your email:

```bash
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --global --list
```

Check individual values:

```bash
git config --global user.name
git config --global user.email
```

### Important

The name and email stored in your Git commits are separate from your GitHub login credentials.

---

# 8. Create a Git Repository

Create a project:

```bash
mkdir git-practice
cd git-practice
```

Initialize Git:

```bash
git init
```

Git creates a hidden `.git` directory.

Check the repository:

```bash
git status
```

---

# 9. What does `git init` do?

Command:

```bash
git init
```

Purpose:

> Initializes the current directory as a Git repository.

Before:

```text
git-practice/
└── file.txt
```

After:

```text
git-practice/
├── file.txt
└── .git/
```

Now Git can track changes in the project.

---

# 10. The Four Important Git Areas

This is one of the most important concepts in Git.

```text
Working Directory
       ↓
    git add
       ↓
Staging Area
       ↓
  git commit
       ↓
Local Repository
       ↓
   git push
       ↓
Remote Repository
     (GitHub)
```

### Working Directory

Where you actually create and modify files.

### Staging Area

Where you select the changes that should go into the next commit.

### Local Repository

Where your commits are stored locally.

### Remote Repository

The repository hosted on GitHub or another Git hosting service.

---

# 11. Working Directory

The working directory contains the files you are currently working on.

Example:

```text
src/
├── App.jsx
├── Navbar.jsx
└── Login.jsx
```

If you modify:

```text
Navbar.jsx
```

Git detects that the file has changed.

Check:

```bash
git status
```

---

# 12. Staging Area

The staging area is where you prepare changes before committing them.

Example:

```bash
git add Navbar.jsx
```

Now the changes to `Navbar.jsx` are staged.

Think of staging as:

> "I want this change to be included in my next commit."

---

# 13. Commit

A commit is a **saved snapshot of staged changes**.

Example:

```bash
git commit -m "Fix navbar spacing"
```

A commit contains information such as:

* Changes
* Author
* Date/time
* Commit message
* Commit hash

Example:

```text
a81f92c
```

The commit hash uniquely identifies that commit.

---

# 14. Basic Git Workflow

The basic Git cycle is:

```text
Modify files
     ↓
git status
     ↓
git add
     ↓
git status
     ↓
git commit
     ↓
git log
```

Example:

```bash
git status

git add .

git commit -m "Add login page"

git log
```

---

# 15. `git status`

Command:

```bash
git status
```

Purpose:

> Shows the current state of your working directory and staging area.

It can show:

* Current branch
* Modified files
* Untracked files
* Staged changes
* Unstaged changes

Example:

```text
On branch main

Changes not staged for commit:
    modified: Navbar.jsx

Untracked files:
    Login.jsx
```

### Good Habit

Run:

```bash
git status
```

frequently.

For example:

```text
Start working
     ↓
git status
     ↓
Make changes
     ↓
git status
     ↓
Before commit
     ↓
git status
```

---

# 16. Untracked Files

Suppose you create:

```text
Login.jsx
```

Git may show:

```text
Untracked files:
    Login.jsx
```

This means Git sees the file but it has not yet been added to the staging area.

Add it:

```bash
git add Login.jsx
```

---

# 17. `git add`

Add one file:

```bash
git add file.txt
```

Add multiple files:

```bash
git add file1.txt file2.txt
```

Add all changes:

```bash
git add .
```

### Important

`git add` does **not** create a commit.

It only moves selected changes into the staging area.

```text
Working Directory
       ↓
    git add
       ↓
Staging Area
```

---

# 18. `git commit`

Create a commit:

```bash
git commit -m "Add login page"
```

### Good Commit Messages

```text
Add login page
Fix navbar alignment
Update vendor form
Add search functionality
Fix duplicate clear button
```

### Bad Commit Messages

```text
changes
update
done
test
final
asdf
```

A good commit message should tell someone **what changed**.

---

# 19. View Commit History

View complete history:

```bash
git log
```

View a compact history:

```bash
git log --oneline
```

Example:

```text
a81f92c Fix navbar alignment
7d92abc Add login page
34c8def Initial commit
```

---

# 20. What is HEAD?

`HEAD` represents your current position in Git history.

Example:

```text
A ─── B ─── C
            ↑
           HEAD
```

When you switch branches, `HEAD` moves to the current branch.

Branches and `HEAD` will be studied in detail later.

---

# 21. What is a Branch?

A branch is a separate line of development represented by a pointer to a commit.

Example:

```text
A ─── B ─── C
            ↑
           main
```

Create another branch:

```bash
git branch feature/login
```

Now:

```text
A ─── B ─── C
            ↑
       ┌────┴────┐
      main   feature/login
```

Branching will be covered in detail in the next lesson.

---

# 22. Connect a Local Repository to GitHub

A remote repository is another copy of your Git repository, usually hosted on GitHub.

Add GitHub as a remote:

```bash
git remote add origin <repository-url>
```

Check the remote:

```bash
git remote -v
```

Example:

```text
origin  <repository-url> (fetch)
origin  <repository-url> (push)
```

`origin` is the commonly used name for the main remote repository.

---

# 23. `git push`

Push sends your local commits to the remote repository.

```bash
git push
```

For the first push of a branch:

```bash
git push -u origin main
```

Concept:

```text
Local Repository
       ↓
    git push
       ↓
GitHub Repository
```

---

# 24. `git pull`

Pull gets changes from the remote repository and integrates them into your current branch.

```bash
git pull
```

Basic idea:

```text
GitHub
   ↓
git pull
   ↓
Local Repository
```

---

# 25. `git clone`

Clone downloads an existing Git repository from a remote location.

```bash
git clone <repository-url>
```

Example:

```bash
git clone https://github.com/user/project.git
```

After cloning:

```text
GitHub Repository
       ↓
   git clone
       ↓
Local Repository
```

---

# 26. `git fetch`

Fetch downloads information about changes from the remote repository without integrating those changes into your current branch.

```bash
git fetch
```

Basic difference:

```text
git fetch
    ↓
Download remote changes/information
    ↓
Do not automatically integrate them
```

Whereas:

```text
git pull
    ↓
Fetch
    +
Integrate changes
```

---

# 27. `git diff`

See changes that haven't been staged:

```bash
git diff
```

See changes that have been staged:

```bash
git diff --staged
```

Compare two commits:

```bash
git diff commit1 commit2
```

---

# 28. `.gitignore`

`.gitignore` tells Git which files or folders should not be tracked.

Example:

```gitignore
node_modules/
.env
dist/
build/
*.log
```

For a Node.js project:

```gitignore
node_modules/
.env
```

### Why ignore `.env`?

It may contain sensitive information:

```text
DATABASE_PASSWORD
API_KEY
AWS_SECRET
```

Never commit secrets to GitHub.

---

# 29. Restore Changes

If you modify a file but want to discard the uncommitted changes:

```bash
git restore filename
```

Example:

```bash
git restore Navbar.jsx
```

This restores the file to its last committed version.

⚠️ Be careful because this can permanently discard uncommitted changes.

---

# 30. Unstage a File

Suppose you run:

```bash
git add Navbar.jsx
```

but then decide you don't want to include it in the next commit.

Use:

```bash
git restore --staged Navbar.jsx
```

This removes the file from the staging area but **keeps your changes in the working directory**.

---

# 31. Most Important Commands

| Command         | Purpose                     |
| --------------- | --------------------------- |
| `git --version` | Check Git version           |
| `git config`    | Configure Git               |
| `git init`      | Initialize repository       |
| `git status`    | Check current state         |
| `git add`       | Stage changes               |
| `git commit`    | Create a commit             |
| `git log`       | View commit history         |
| `git diff`      | View changes                |
| `git branch`    | Manage branches             |
| `git switch`    | Switch branches             |
| `git merge`     | Merge branches              |
| `git remote`    | Manage remote repositories  |
| `git clone`     | Clone a repository          |
| `git fetch`     | Download remote information |
| `git pull`      | Fetch and integrate changes |
| `git push`      | Upload commits              |
| `git restore`   | Restore/discard changes     |

---

# 32. Complete Git Flow

The basic flow is:

```text
                Make Changes
                     ↓
              Working Directory
                     ↓
                  git add
                     ↓
               Staging Area
                     ↓
                git commit
                     ↓
              Local Repository
                     ↓
                 git push
                     ↓
              GitHub Repository
```

---

# 33. Git vs GitHub

### Git

```text
Git
│
├── commit
├── branch
├── merge
├── rebase
├── stash
├── reset
├── revert
└── log
```

### GitHub

```text
GitHub
│
├── Repository
├── Pull Request
├── Issues
├── Code Review
├── GitHub Actions
└── Releases
```

---

# 34. What I Learned Today

After studying this topic, I should understand:

* What Git is
* What GitHub is
* Difference between Git and GitHub
* What version control means
* What a repository is
* Local vs remote repository
* Working directory
* Staging area
* Local repository
* `git init`
* `git status`
* `git add`
* `git commit`
* `git log`
* `HEAD`
* Basic idea of branches
* `git remote`
* `git push`
* `git pull`
* `git clone`
* `git fetch`
* `git diff`
* `.gitignore`
* `git restore`

---

# 35. Practice I Completed

### Basic repository setup

```bash
git init
git status
```

### Staging and committing

```bash
git add .
git commit -m "Complete Git basics practice"
```

### Viewing history

```bash
git log --oneline
```

### Remote repository

```bash
git remote -v
git push
```

---

# 36. Questions I Should Be Able to Answer

Before moving to the next topic, I should be able to answer:

1. What is Git?
2. What is GitHub?
3. What is the difference between Git and GitHub?
4. What is a Git repository?
5. What does `git init` do?
6. What is the working directory?
7. What is the staging area?
8. What does `git add` do?
9. What does `git commit` do?
10. What is a commit?
11. What does `git status` show?
12. What does `git log` show?
13. What is `HEAD`?
14. What is a branch?
15. What is the difference between local and remote repositories?
16. What does `git push` do?
17. What does `git pull` do?
18. What does `git fetch` do?
19. What does `git clone` do?
20. Why do we use `.gitignore`?

---

# 37. Key Takeaways

```text
Git = Version Control System

GitHub = Online platform for Git repositories

Repository = Project tracked by Git

Working Directory = Where I make changes

Staging Area = Changes prepared for commit

Commit = Saved snapshot of changes

Branch = Separate line of development

Push = Local → Remote

Pull = Remote → Local + integrate

Fetch = Get remote information without integrating

Clone = Copy an existing remote repository
```

## Most Important Workflow

```bash
git status
git add .
git commit -m "Meaningful message"
git push
```

This is the basic Git workflow I will use repeatedly while learning and working with Git.
