# easy-server-actions

This workflow is triggered on a push event to the master branch and consists of a single job with four steps. The first step checks out the code, the second step sets up Node.js, the third step installs the dependencies, and the fourth step runs the server.

You can customize this workflow to suit your specific needs. For example, you might want to run different commands depending on the type of event (e.g. a push to a different branch, a pull request) or run additional steps for testing and deployment.

## Options

There are several alternatives to npm (the Node Package Manager) that can be used to manage dependencies in Node.js projects. Here are a few options:

1. yarn: Yarn is a package manager developed by Facebook that is designed to be faster and more reliable than npm. It uses a cache to ensure that packages are installed consistently across different environments, and it also has features for managing workspaces and controlling version constraints.

2. pnpm: pnpm is a package manager that is focused on reducing disk space usage and network traffic. It uses a shared store to reduce the number of copies of each package that need to be installed, and it also has features for managing multiple versions of the same package.

3. ied: ied is a package manager that is designed to be simple and easy to use. It has a minimalist command set and integrates with the system package manager (e.g. apt on Ubuntu) to reduce the number of dependencies that need to be installed.

There are also other package managers available for Node.js, such as npm-check and npm-install-missing, that offer additional functionality or address specific use cases. You can choose the package manager that best fits your needs and workflow.

### Will the action in github run the in the background?

By default, the steps in a GitHub Actions workflow run in the foreground, meaning that they are executed one after the other and the workflow will not complete until all steps have finished running. However, you can use the & operator at the end of the command to run the server in the background as a child process of the shell.

For example, you can modify the npm start step in your workflow as follows:

      - run: npm start &

This will cause the server to be started in the background and the workflow will continue to the next step without waiting for the server to complete. The server will continue running as long as the workflow is active, and it will be terminated when the workflow completes or is cancelled.

Keep in mind that the & operator only works on Unix-like systems (such as Linux and macOS), and it may not be available on other platforms. If you need to run the server in the background on a different platform, you will need to use a different method, such as a process manager or a screen/tmux session.
