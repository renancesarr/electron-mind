# Electron Mind - A Productivity Tool with Emotional Intelligence

## Overview

Electron Mind is a unique productivity application designed to create a focused and intentional workspace where users can manage tasks and reduce distractions in an integrated way. This tool goes beyond traditional to-do lists by offering a space that monitors progress, suggests strategic breaks, and analyzes patterns of focus and performance, allowing users to gain deeper insights into their own behaviors and priorities.

Built with an agile-inspired approach, Electron Mind combines elements of Kanban and Scrum with positive psychology triggers to provide a personalized and motivating productivity experience. With an intuitive interface and features that limit multitasking, users can focus on one task at a time while tracking visual metrics of completed and abandoned tasks. This constant feedback reinforces motivation and helps maintain focus on clear goals.

This open-source project is ideal for developers, individuals with ADHD, and any productivity enthusiast seeking a smart, user-centered approach. With Electron Mind, the goal is to create a digital environment that not only boosts productivity but also fosters a deeper understanding of individual habits and preferences.

Future plans for Electron Mind include incorporating artificial intelligence features to suggest tasks based on priorities and behavior patterns, as well as integrating digital environment controls to block distracting apps or websites.This open-source project is ideal for developers and productivity enthusiasts seeking a smart, user-centered approach to enhancing their workflow.

This tool is particularly aimed at users with ADHD or anyone seeking to improve their productivity by managing task priority and tracking time effectively.

## General Architecture

1. Interface Layer (Front-End)

    Technologies: React with TypeScript for scalability and Tailwind for styling. The interface is based on a dynamic Kanban board with columns like Backlog, Executing, Abandoned, and Completed.
    Key Components:
        Dynamic Kanban Board: Includes animations for a more visual and functional flow.
        Lock and Trigger Components: Interactive modals that appear at critical moments to maintain focus.
        Metrics and Feedback Dashboard: Shows progress charts (such as abandoned vs. completed) with daily, weekly, and monthly metrics.
    Widgets: Adaptable interface for desktop and mobile devices.

2. Logic and Control Layer (Back-End)

    Technologies: Node.js with Express or Python with FastAPI, depending on machine learning integration needs.
    Main Modules:
        Task Management: Controls real-time task status.
        Focus and Time Trigger Control: Triggers that monitor time and focus, activating notifications when needed.
        Contextual Lock System: Integrates with Electron to manage blocked apps and domains while a task is active.

3. Database Layer (Persistence)

    Primary Database: PostgreSQL to store task information, history, and status.
    Cache: Redis for session data and real-time trigger support.
    Data Structure:
        Task Table: Fields for title, description, status, and estimated vs. actual time.
        History Table: Detailed records of status changes and time spent.
        Insights Table: Aggregated data to suggest new tasks and improve performance.

4. Flow Control and Triggers

    Notifications and Triggers: Event listeners trigger locks and notifications, such as:
        On Moving to Executing: Starts the timer and blocks unauthorized apps.
        Post-Task Feedback: After completing a task, asks about success and suggests improvements.

5. AI and Suggestion Intelligence Layer

    Recommendation Intelligence:
        Machine Learning Model: Clustering and neural networks to identify task patterns.
        Adaptive Priority Model: Suggests tasks based on user patterns and behaviors.
    Productivity Analysis: Compares estimated vs. actual time to improve estimates and planning.

6. Contextual Lock and Control Integration

    Application and Site Management: Blocks apps and domains, using Electron for complete desktop integration.
    Browser and System Plugins: Extensions and direct OS control to ensure a focus-driven environment.


## Project Guidelines and Best Practices

This project follows best practices and coding standards outlined in two comprehensive repositories:

1. [Node.js Best Practices by Yoni Goldberg](https://github.com/goldbergyoni/nodebestpractices): This repository covers over 80 best practices, design patterns, and coding styles specific to Node.js applications. It provides guidelines for structuring projects, handling errors, ensuring security, and much more. By following these practices, we aim to maintain a clean, robust, and efficient codebase.

2. [Project Guidelines by Elsewhen](https://github.com/elsewhencode/project-guidelines/): This repository focuses on general software development guidelines that apply to any project. It includes recommendations for Git workflow, code structure, documentation, and code review processes. These guidelines help us maintain consistency, readability, and collaboration standards across the project.


## Git Workflow

Following these Git workflow guidelines will help keep the repository organized and enhance collaboration. For more details, refer to the [Project Guidelines](https://github.com/elsewhencode/project-guidelines#git-workflow).

1. Creating a New Feature or Bug-Fix Branch

Checkout a new branch for each feature or bug-fix:

```bash
git checkout -b <branchname>
```

2. Making Changes and Committing

Make your changes and add only the relevant files for a concise commit:

```bash
git add <file1> <file2> ...
git commit
```
Why?

    git add <file1> <file2> ...: Add only files with small, concise changes to keep commits focused.
    git commit: Opens an editor, allowing you to separate the commit title from the body message.

Tip: Use git add -p to review each change and decide if it should be included in the commit.

3. Syncing with Remote Develop Branch

Before pushing, synchronize your feature branch with the latest changes from the remote develop branch:

```bash

git checkout develop
git pull
```

Why?

    This allows you to handle conflicts locally while rebasing instead of creating a pull request with conflicts.

4. Rebasing Your Feature Branch

Update your feature branch with the latest changes from develop using an interactive rebase:

```bash
git checkout <branchname>
git rebase -i --autosquash develop
```

Why?

    Using --autosquash combines all your commits into a single commit for a cleaner history. Development commits don’t need to clutter the main history.

5. Handling Conflicts (If Any)

If there are no conflicts, you can skip this step. If conflicts appear, resolve them, then continue the rebase:

```bash

git add <file1> <file2> ...
git rebase --continue
```

6. Pushing Your Branch

After rebasing, push your branch. Since rebase alters history, use the -f flag to force the update. If others are working on the same branch, consider using --force-with-lease for added safety.

```bash
git push -f
```

Why?

    Rebasing changes the history of your feature branch. Git will reject the push unless you use -f or --force.

7. Opening a Pull Request

Once your branch is up-to-date with develop and all changes are pushed, open a pull request for review.

