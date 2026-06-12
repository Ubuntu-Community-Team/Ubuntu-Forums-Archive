---
title: "Different settings depending on login method"
date: 2012-06-22
forum: General Help
---

### Post by Brundle on 2012-06-22
Hi,

I'm running Ubuntu 12.04 32 bit server version. I've just set up public/private key authentication using Putty, and I noticed that my shell environment appears slightly different depending on whether i log in using the private key or type in my password.

For example, if I log in using private key and type ls, this is what I get:

edpba@Porter:~$ ls
Access-Your-Private-Data.desktop  README.txt
edpba@Porter:~$

If i log in using username/password and do the same thing i get:

edpba@Porter:~$ ls
edpba@Porter:~$

Also, if I type "echo $" and hit tab I get different lists of environment variables, indicating that my environment is somehow different depending on the method of authentication. 

I don't know where to start looking for information on this  (sshd man pages?, bash man pages?, Putty documentation?), but I would like to understand what the difference between login methods is (what scripts are run, which environment variables are set etc), so if anyone could point me in the right direction it would be greatly appreciated.

//Brundle

---

### Post by Paddy Landau on 2012-06-23
You clearly have encryption on your home folder.

When you log in with your username and password, the computer decrypts your home folder.

When you log in with your key, the computer does not have access to your password, so it cannot decrypt your home folder.

Once you have logged in with your key, you will have to decrypt your home folder manually using your password. 

Unfortunately, encryption on Ubuntu is terribly documented, and so I don't know how to do this manually (otherwise I'd tell you).

I believe — but I have **not** tested this — that the command would be as follows (replace Brundle with your user name):
```
sudo mount -t ecryptfs /home/.ecryptfs/Brundle/.Private /home/Brundle/
```The command asks several questions. The first is your passphrase, which is in fact your login password; and I don't know the answers to the remainder, sorry.

---

### Post by Brundle on 2012-06-23
> **Paddy Landau said:**
> You clearly have encryption on your home folder.

When you log in with your username and password, the computer decrypts your home folder.

When you log in with your key, the computer does not have access to your password, so it cannot decrypt your home folder.

Once you have logged in with your key, you will have to decrypt your home folder manually using your password. 

Unfortunately, encryption on Ubuntu is terribly documented, and so I don't know how to do this manually (otherwise I'd tell you).

I believe — but I have **not** tested this — that the command would be as follows (replace Brundle with your user name):
```
sudo mount -t ecryptfs /home/.ecryptfs/Brundle/.Private /home/Brundle/
```The command asks several questions. The first is your passphrase, which is in fact your login password; and I don't know the answers to the remainder, sorry.

Thank you for your quick response, that got me quite far, although my problem isn't quite solved. I tried the mount-command you mention, but didn't get very far as I don't know the answers to all the questions either. However I did find that there is a script provided, /usr/bin/ecryptfs-mount-private, which only requires the password in order to decrypt my home directory.

If I run this command and then start a second SSH-session in a new Putty-window, it seems my .bashrc is processed and I get my ls-output in color and things are the way I would like them to be. However, in my first SSH-session my environment stuff is still wrong.

I'm thinking there must be some way to automatically decrypt the directory upon starting an SSH-session? Browsing through the ecryptfs-mount-private, I see there's a reference to a key on a keyring, don't know if that's a clue. Does anyone know?

---

### Post by cool110 on 2012-06-23
AFAIK there's no way of mounting an encrypted home without entering the password. 
However as a workaround you could move your .bashrc, .profile, Maildir, etc. to another location and symlink them both with and without your home mounted.

---

### Post by Paddy Landau on 2012-06-23
Brundle, thanks for the ecryptfs-mount-private. That is worth remembering.

> **cool110 said:**
> AFAIK there's no way of mounting an encrypted home without entering the password.
There is a way, but it requires you to know the two 32-character keys, and is therefore much harder than just entering your password.

> **cool110 said:**
> However as a workaround you could move your .bashrc, .profile, Maildir, etc. to another location and symlink them both with and without your home mounted.
That would work provided that they did not require any files from the user's (decrypted) folder. You could even have .bashrc check whether or not the folder had been encrypted and, if not, run ecryptfs-mount-private for you, so you'd only have to enter your password and not the command.

BTW, the typical user would need only .profile and .bashrc.

Try it and let us know whether or not it works.

---

