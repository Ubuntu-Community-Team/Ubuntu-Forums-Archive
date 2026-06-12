---
title: "Login Problems, please help!!!"
date: 2009-10-30
forum: General Help
---

### Post by windsong on 2009-10-30
So here's my problem...
 
After I enter the user name and password I get a "pop up" message saying the following: 
User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users. 
 
If I hit "OK" (which is the only option) I get a second "pop up" message saying the following: 
GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator. 
 
After hitting "OK" again (which again is the only option) the screen goes black then brings me back into the "Log In" menu.
 
I'm not exactly the smartest when it comes to computers... would someone be able to explain in "dummy" terms how to fix this please?

---

### Post by lilbill on 2009-10-30
It sounds as though the permissions got changed for the directories/files.

First, you will need to boot into recovery mode.  To do this turn on the computer and follow these instructions [https://wiki.ubuntu.com/RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode").

Note for each command below, enter one line at a time and press return to execute the command.
Now we will navigate to the /home directory type
```
cd /home
ls -l

```
You should see output like
```

drwxr-xr-x 41 dear dear  4096 2009-10-30 22:17 dear
drwx------  2 root root 16384 2009-10-29 16:50 lost+found

```
Now, we need to change the owner of your directory (the one that corresponds to your username, the last entry in the row is the folder name)

If the line of your named directory is drwxr-xr-x xx yourname yourname ...
then, this will not help.  Otherwise we will continue.

Now type
```

chown yourUserName yourDirectoryName
chmod 755 yourDirectoryName

```
where UserName is the one you log in with and Directory name is the one shown above.

Now change to your directory and change the file's permissions
```

cd yourDirectoryName
chmod 644 .dmrc

```

Great, now type exit and choose resume normal boot and try to login.

Hope that helps!

---

### Post by JBAlaska on 2009-10-30
What lilbill said:

```
sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod -R 700 /home/username
sudo chown -R username /home/username
```

Sub username for ..well your username

---

### Post by lilbill on 2009-10-30
Thanks...the absolute path commands would have been much easier to describe!

---

### Post by shadowlands on 2009-10-30
> **JBAlaska said:**
> What lilbill said:

```
sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod -R 700 /home/username
sudo chown -R username /home/username
```

Sub username for ..well your username

this happen to me also.  I think.  When I type in the info it tells me my username is not found.  

What I doing wrong?  Thanks in advance correction I have items that failed to mount.

---

