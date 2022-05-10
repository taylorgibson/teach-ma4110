# SSH keypair setup for GitHub (or GitHub/GitLab/BitBucket, etc, etc)


## Create your repository.
Make sure there is at least one file in it (even just the README.md)


## Generate a SSH key pair (private/public):

```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## Set permissions on the private SSH key

Github is very strict about key security. They will not allow you to connect if your private key can be read by anyone
```
cd ~/.ssh/
chmod 600 id_rsa
```

## Display the contents of the public SSH key

The following command will display the public key.

```
cat ~/.ssh/id_rsa.pub
```

highlight it and press `ctrl + C` (windows) or `option + C` (mac) to copy it to the clipboard.


## Copy the public SSH key to GitHub
Copy the contents of your public SSH key to your GitHub account settings (https://github.com/settings/keys).


## Test the SSH key:
```
ssh -T git@github.com
```

Change directory into the local clone of your repository (if you're not already there) and run:
```
git remote set-url origin git@github.com:username/your-repository.git
```

Now try editing a file (try the README) and then do:
```
git add -A
git commit -am "Update README.md"
git push
```

You should not be asked for a username or password. If it works, your SSH key is correctly configured.
