# [LLM Prompt Editor App](https://github.com/RocketChat/Apps.LLM.PromptEditor) for [Rocket.Chat](https://rocket.chat/)

# Project Overview and Goals
## Overview
This project was developed during GSoC 2024 and involved the creation of a Rocket.Chat app called LLM Prompt Editor. The app integrates Golem, a prompt editor, with Rocket.Chat's in-house AI models to provide advanced prompt editing and AI inference capabilities directly within Rocket.Chat.

## Goals
1. **Create a Prompt Editor**: Develop an LLP (Large Language Model) prompt editor using Golem.
2. **Decouple Inference Functionality**: Replace Golem's existing OpenAPI inference with Rocket.Chat’s in-house AI models.
3. **Support Streaming**: Implement concurrent streaming of responses across multiple devices.
4. **Integrate with Rocket.Chat**: Bundle the Golem editor and serve it through a Rocket.Chat app.
5. **API Endpoints**: Develop API endpoints in the app to serve the Golem build.
6. **Data Persistence**: Store chat history in Rocket.Chat's MongoDB for future inference.
7. **Conversation History API**: Provide an endpoint for Golem's frontend to request conversation history.
8. **App Commands**: Create Rocket.Chat app commands to initiate workflows from the main Rocket.Chat instance.

## Challenges Faced
### 1. Decoupling Inference
The process of decoupling Golem's behavior from OpenAPI inference was complex due to the numerous hooks involved.

### 2. Fetching and Rendering Data
Similarly, fetching and rendering conversation data posed challenges due to the hooks.

### 3. Vite Packaging Issues
Golem used Vite for packaging, which by default splits JavaScript into multiple files. For this project, it was crucial to minimize the number of files, requiring significant adjustments.

## Demo Video
The demo includes a video showcasing the following features:

https://github.com/user-attachments/assets/ffae49c9-caa5-40a3-bd31-4ddd93f52a80

### Concurrency and Streaming
Demonstration of how the app supports concurrent streaming of responses through Golem rendered via the Rocket.Chat app.

### Steps Demonstrated
#### 1. Initiating a Prompt
How to start a prompt editing session using the LLM Prompt Editor in Rocket.Chat.

#### 2. Streaming Responses
Visualization of how responses are streamed and handled concurrently across different devices.

#### 3. Saving and Fetching Conversation History
Demonstration of how chat history is saved in MongoDB and how it can be retrieved for future use.

#### 4. Using App Commands
Explanation of how to use the custom Rocket.Chat app commands to interact with the LLM Prompt Editor.


## Local Setup Guide

#### Make sure you have a working Rocket.Chat server and Apps-Engine CLI for your machine. You can setup the server for your local machine from [here](https://developer.rocket.chat/open-source-projects/server/server-environment-setup) and CLI from [here](https://developer.rocket.chat/apps-engine/getting-started/rocket.chat-app-engine-cli).

1. Navigate to the `client` folder:

   ```bash
   cd Golem
   ```

2. Install all required packages:

   ```bash
   pnpm install
   ```

3. Build the webpack bundle for the Excalidraw React app:

   ```bash
   pnpm run generate
   ```

4. Execute the build.js script to generate build scripts for `bundle.ts`

   ```bash
   npm run build:golem
   ```

5. Change directory to `LLM App` and install all Rocket chat app packages :
   ```bash
   cd ../LLM App/
   ```
   ```bash
   npm install
   ```
6. Deploy your app locally

   ```bash
   rc-apps deploy --url http://localhost:3000 --username ${username} --password ${password}
   ```

   Your username and password are your local server's user credentials .Verify the successful build by accessing the `/excalidraw` endpoint in the Whiteboard app settings. You can access the React app through the provided URL.

### Instead of running the above commands, you can simply use the shortcut commands

1. #### You can use the Makefile to run the server as well

   ```bash
   make YOUR_USERNAME=${username} YOUR_PASSWORD=${password}
   ```

   Make sure to replace ${username} and ${password} with the actual username and password values of your local server's user credentials. Alternatively, you can modify the Makefile directly by replacing the USERNAME and PASSWORD variables.

   #### Additional Commands:

   For build:

   ```bash
   make build YOUR_USERNAME=${username} YOUR_PASSWORD=${password}
   ```

   For deploy:

   ```bash
   make deploy YOUR_USERNAME=${username} YOUR_PASSWORD=${password}
   ```

## Gitpod Setup Guide

Follow these steps to set up your development environment using Gitpod:

1. **Visit Gitpod Website:**

   - Go to [Gitpod](https://www.gitpod.io/) and click on the dashboard.

2. **Login with GitHub:**

   - Login to Gitpod using your GitHub account credentials.

3. **Create a New Workspace:**

   - Click on the "New Workspace" button.
   - In the dropdown menu, select the repository you want to work on, specifically the `Apps.LLM.PromptEditor` repository that you've previously forked on GitHub.

4. **Continue and Wait:**

   - Click "Continue" and give it some time to initialize your workspace.

5. **Start Coding:**
   - After a few seconds, you'll see a fully-functional code editor in your browser.
   - Feel free to start coding, making changes, and contribute to the `Apps.Whiteboard` repository.

That's it! You are now set up and ready to contribute. If you encounter any issues or have questions, refer to the [Gitpod documentation](https://www.gitpod.io/docs/) or reach out to the community for assistance.

Happy coding!


## Future Enhancements
### 1. Improving Hook Management
Continued efforts to streamline the handling of hooks in Golem.

### 2. Enhanced Packaging
Further optimization of the Vite packaging process to suit the app’s needs.

## 🤝 Appreciations
Here to expresses my sincere gratitude to my mentors and provide my profile details for networking

### ✨ Gratitude to Mentors
I would like to express my sincere gratitude to my amazing mentors Gabriel Engel, Sing Li, John Crisp and Shubham Bhardwaj, for their invaluable guidance and support throughout my GSoC'24 journey 🚀. Their constant encouragement, technical expertise, and willingness to help have been instrumental in the success of this project. I feel incredibly fortunate to have had the opportunity to learn from such talented individuals. 🌟

I would also like to extend a heartfelt thank you to the entire Rocket.Chat developer community for their openness and support throughout the development process. Thank you both for your mentorship and for inspiring me to learn and grow beyond GSoC. 🙏
