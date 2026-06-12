---
title: "How to apply parent permissions to all subfolders and files?"
date: 2010-05-16
forum: General Help
---

### Post by travlemon on 2010-05-16
Hello!

I'm having a problem with folder/file permissions in Ubuntu.  I have a box running Ubuntu 10.04, that is pretty much going to be a NAS.  I'm using it to store files/folders, and sharing them over a network for users to access. 

To start off, I must say that root is the user I sign on as and leave the machine running under that user.  The files/folders used to be on an NTFS partition, shared through Windows.  I moved everything, as root, over to an EXT4 partition that I had created.  There are many subfolders that I'd have to set permissions on, so this is what I did (as Windows does this with no problems):

I used Ubuntu Tweak to reveal advanced permission settings. Then, I right click the parent folder and go to the Permissions tab.  I set the Owner, and then the Group from the drop down menus.  I choose which permissions each should have (read, write, or execute).  Then, I click "Apply Permissions to Enclosed Files". 

It looks like this applies the permissions corresponding to Owner, Group, and Others.  However, it doesn't actually change the Owner or Group to what I selected in the parent folder.  This leaves me to manually go to every single folder (there are tons), and right click each one invidually and choose the proper Owner and Group.

Can anyone help me out with this? This is quite inconvenient and primative of a method to mirror the permissions of a parent folder to it's children folders. Any assistance in clearing up this issue would be a HUGE help, as I have a huge amount of folders I'd have to set permissions on.

A side note:  I tried using the checkboxes "Set GID", "Set UID", and "Sticky"...but they don't seem to make a difference.

Thanks in advance!

---

### Post by rookcifer on 2010-05-16
What do you want the permissions to be on the individual files?  It's actually easier to just use the terminal and the [octal system]("https://help.ubuntu.com/community/FilePermissions") (rwx = 4-2-1).  So, for instance, if you wanted the files to have rwx permissions for the owner, but no permissions for the group or other, you would do:

```
sudo chmod 0700 /name/of/file
```

If you wanted to apply the same permissions to each file within a directory, you add the -R flag like this:

```
sudo chmod -R 0700 /directory
```

At any rate, until you learn this system, tell me what permissions you want the files to have and I'll give you the command to run.

---

### Post by travlemon on 2010-05-16
> **rookcifer said:**
> What do you want the permissions to be on the individual files?  It's actually easier to just use the terminal and the [octal system]("https://help.ubuntu.com/community/FilePermissions") (rwx = 4-2-1).  So, for instance, if you wanted the files to have rwx permissions for the owner, but no permissions for the group or other, you would do:

```
sudo chmod 0700 /name/of/file
```If you wanted to apply the same permissions to each file within a directory, you add the -R flag like this:

```
sudo chmod -R 0700 /directory
```At any rate, until you learn this system, tell me what permissions you want the files to have and I'll give you the command to run.

Hey, thanks for responding so quick! I actually just answered my own question when I realized that chown and chgrp are exactly what I need.  The commands I ran (before I saw you replied) were:

chown -R username folder
chgrp -R username folder

I realized the "Apply Permissions to Enclosed Files" applies everything on the permissions tab to the subfolders, except the Owner and Group.  While chown and chgrp change ONLY the Owner or Group. 

I'm going to mark this as solved.  Thank you for your help though!

---

### Post by bodhi.zazen on 2010-05-17
Moved to general help.

---

### Post by Francewhoa on 2010-10-22
Another way of doing this with a visual interface [http://ubuntuforums.org/showthread.php?t=1454684](http://ubuntuforums.org/showthread.php?t=1454684)

---

