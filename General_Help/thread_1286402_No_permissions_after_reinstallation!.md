---
title: "No permissions after reinstallation!"
date: 2009-10-08
forum: General Help
---

### Post by snakeman21 on 2009-10-08
I keep a backup of all of my files on a 230GB external HD.  I have used it to restore my files on fresh installs multiple times without any issues.  This time, however, I had a problem.  

First of all, I didn't have permissions to copy my files from the drive to the computer.  I ran gksudo nautilus so I could copy them.  This worked, but now, even though my files are on my computer's HD, I do not have permissions to modify or move them.  I have literally thousands of files, so changing the permissions of each one is out of the question.  I tried changing the permissions of a folder and selecting "apply permissions to enclosed files" but it did not change anything.  What can I do?

---

### Post by quixote on 2009-10-10
Can you not access root commands at all, ie cannot use sudo, or is it just that ownership of the files has changed to someone else?

Display one of those directories in nautilus, go to View > Visible Columns, and tick Permissions, Owner, and Group.  Are you the owner, but permissions are just all dashes?  Or is root the owner?

There is an easy command line way to change all that recursively, when nautilus acts up.  ```
man chmod   *for more info on changing permissions*
man chown   *for more info on changing owner*
```

to change recursively, cd to the directory that includes all the ones you want to change and then run something like the second command:```
cd /home/you/transferred-files/
sudo chown -R you   *(assuming root is the current owner)*
```

---

### Post by scouser73 on 2009-10-10
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by snakeman21 on 2009-10-10
> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

As I stated in my first post, I tried that, but it DID NOT WORK.

---

### Post by chamira on 2009-10-10
I wonder if the problem is permissions on your new drive is only owned by root. 

You may need to give full access to the new drive.

I had a similar problem with adding a second hdd and I found this blog post:

[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

I hope this is useful.

---

### Post by mechro on 2009-10-10
> **snakeman21 said:**
> As I stated in my first post, I tried that, but it DID NOT WORK.

Quixote (2nd post in thread) has given you a good solution with the code at the end of his/her post.

---

