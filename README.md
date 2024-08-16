# Configuring GitHub on CentOS: Step-by-Step Guide

This guide will walk you through the process of setting up GitHub on a CentOS server. You'll need the following:

- A CentOS server with root or sudo access
- A GitHub account
- An SSH key pair

## Steps to Configure GitHub on CentOS

1. Install Git

Git is a version control system that helps you track changes in your code and collaborate with others. You can install Git on CentOS by running the following command:

```bash
sudo yum install git
```

2. Create a GitHub Account

If you don't already have a GitHub account, you can create one by visiting GitHub's signup page. GitHub provides various plans, including free and paid options for hosting your code.

3. Create an SSH Key Pair

SSH keys are used to securely authenticate your connection to GitHub. You can either use an existing SSH key pair or generate a new one.

Check for Existing SSH Keys:

Before creating a new SSH key, check if you already have one by running:

```sh
ls -al ~/.ssh
```

If you see id_rsa and id_rsa.pub, you already have an SSH key pair that you can use.

Generate a New SSH Key (Optional):

To create a new SSH key pair, use the following command (replace "your_email@example.com" with your GitHub email address):

```sh
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Press Enter to accept the default file location and choose whether to use a passphrase.

Start the SSH Agent:

Ensure the SSH key is loaded into memory by starting the SSH agent:

```sh
eval "$(ssh-agent -s)"
```

After generating the key, ensure that the permissions are correctly set

```sh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
```

Add Your SSH Key to the SSH Agent:

Use the following command to add your private SSH key to the agent:

```sh
ssh-add ~/.ssh/id_rsa
```

Copy Your Public Key:

Copy your public SSH key to the clipboard using one of these commands:

```sh
xclip -sel clip < ~/.ssh/id_rsa.pub
```

or

```sh
cat ~/.ssh/id_rsa.pub
```

4. Add Your SSH Key to Your GitHub Account

To link your SSH key to your GitHub account:

- Log in to GitHub and click on your profile icon in the top-right corner.
- Go to "Settings" > "SSH and GPG keys."
- Click "New SSH key," give it a name (e.g., "CentOS server"), and paste your public key into the "Key" field.
- Click "Add SSH key" to save it.
