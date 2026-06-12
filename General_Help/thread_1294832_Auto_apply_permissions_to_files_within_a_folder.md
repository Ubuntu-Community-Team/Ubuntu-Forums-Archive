---
title: "Auto apply permissions to files within a folder?"
date: 2009-10-18
forum: General Help
---

### Post by Roasted on 2009-10-18
/media/storage is my samba share. In the smb.conf, I have "force group" in there to force the group smbusers on any file/folder that is dropped within that directory for a reason. That's fine - through Samba.

If on my local machine I drop a file in there for samba users to access, it just gets created as jason:jason, not jason:smbusers like I want.

Is there a way to get all files/folders within /media/storage to take on the ownership + group ownership automatically?

---

### Post by Sam on 2009-10-18
Use the setgid bit to auto apply ownership when creating new files or directories:
```
sudo find /media/storage -type d -exec bash -c "chgrp smbusers {} && chmod g+s {}" \;
```
(this set group ownership and setgid bit to all directories within /media/storage)

---

### Post by Roasted on 2009-10-18
It'd be real nice if the bug was fixed for the GUI option under properties - permissions tab for "Apply these permissions to all files and folders." But it seems like that's a bug that's been existent... forever.

---

### Post by Sam on 2009-10-18
Which bug are you referring to ?

---

### Post by Roasted on 2009-10-18
[https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/165113](https://bugs.edge.launchpad.net/ubuntu/+source/nautilus/+bug/165113)

---

### Post by Roasted on 2009-10-19
Read the comments below in the bug report. What are they referring to? Is this suggesting the bug will be fixed in 9.10??

EDIT - It looks like it indeed works for changing permissions. It worked in my 9.10 virtual machine as well as 9.04 here on my computer. However, it does NOT bring the group down. If I change the group ownership in the GUI (even if I own the folder), it doesn't bring down the changes on group ownership. But if I change any octal rights in the GUI and hit apply to etc etc, it changes them accordingly.

---

### Post by Roasted on 2009-10-19
EDIT II - It also looks like it doesn't adjust permissions to actual files, but only folders. 

I just added a bunch of jpg and png files, along with empty folders, to 1 folder. When I use that button to apply permissions to etc etc, it only applies it to the folders inside and not the actual files themselves as well.

I can however, run chmod -R 775 folder at terminal without root and it runs fine, but that's because I own the folder everything else is in, so I can execute that without root.

It's just weird it would do it for folders but not files. Unless it's intended to work as it currently does. I noticed this post in the bug report. 

"In Linux, file permissions are more important than directory permissions. For example the /etc directory contains your systems config files, if you were to change permissions on the /etc and all files underneath you are likely to break the system or open it up to hackers. If feature is to be implemented, there should be limit to only the directories beneath the users home directory. "

Kind of makes sense then. I can change directory permissions from the GUI, yet I can't change individual file permissions. Kind of goes along the same lines as described above. I just wonder if it's a true bug or if it's just considered a bug from people who don't know how to utilize it for its actual purpose.

---

### Post by Sam on 2009-10-19
Bug or feature, who knows ?


BTW if you wish to change permissions/ownership from the terminal, instead of doing a recursive chmod (chmod -R 775) that sets execution bit to files, you can use this:

```
find /path/to/dir -type d -exec chmod 775 {} \;
find /path/to/dir -type f -exec chmod 664 {} \;
```

---

### Post by sisco311 on 2009-10-19
> **Roasted said:**
> 
Is there a way to get all files/folders within /media/storage to take on the ownership + group ownership automatically?

setgid & acl 

[http://ubuntuforums.org/showpost.php?p=1193555&postcount=13]("http://ubuntuforums.org/showpost.php?p=1193555&postcount=13")

---

### Post by Roasted on 2009-10-20
> **sisco311 said:**
> setgid & acl 

[http://ubuntuforums.org/showpost.php?p=1193555&postcount=13]("http://ubuntuforums.org/showpost.php?p=1193555&postcount=13")

I don't mean to sound like an idiot, but what in that link is pertaining to me?

I have no problem using terminal. In fact, I prefer it. It's just when I see GUI options there I like to try them out and see how they work, and I found it strange I could get terminal working yet the GUI part wasn't. I thought it was something I was doing wrong. But then again, that one guy had a good point. You don't want to make the GUI too powerful, or else the wrong features will get enabled or executed without really wanting it... especially for us click happy users. :P

Why is it I wouldn't want the execute permissions to flow down?

In terms of setting permissions, I found something that works out even easier for me. I didn't realize that you could CD into a directory and just run chmod 777 * and it would change everything inside to 777 permissions.

There are places I want to use 770 permissions in 1 directory, and everything within that directory to use 775 permissions. Before, I would run:

chmod -R 775 /path/folder

then, 775 permissions would be on the root folder + everything inside, but I want 700 on that folder, not 775... so I'd have to run

chmod 770 /path/folder

to get the desired result. So as a result, running chmod 777 * or whatever perms you want to set with the * wildcard is an easy way to change everything INSIDE a directory. It at least cuts down the amount of commands I need to run to get done what I need. :)

---

### Post by Roasted on 2009-10-23
Bumping this up to build more discussion on it.

I noticed something. I tested this by adding some mp3 files, jpg files, and empty folders to 1 folder. The default permissions for when you create a folder seems to be 755, so the permissions came down as such.

I added the files to the folder in question and naturally they all got jason:jason 755 permissions.

On the "apply permissions to enclosed files" button, it says just that - apply PERMISSIONS. And it works fine. It does indeed pull the permissions (not group - just permissions) when you apply that button.

But the thing I noticed was, mp3 files and jpg files still stayed at 755 permissions.

The big question is - is that because you can't necessarily "write" to a mp3 or jpg file? If I use chmod -R 775, it does apply 775. But I can't help but to wonder and assume that Linux seems to know that you can't "write" to those kinds of files like you can to a folder or anything. Plus - it also seems that individual file permissions don't "necessarily" matter since it takes on the directory's permissions.

Example - folder owned by pam:smbusers (I'm a member of smbusers) with 775 permissions. Yet the group permission on the individual text file within the folder is "read only" so I expected I wouldn't be able to write to that file. Yet, I can. So the 775 permissions on the folder "x" allowed me to write to a text file within "x" when the individual text file inside had read-only permissions for group - aka me.

Sorry I'm just talking out loud to try and understand this better. It's actually very simple once you think about it.

---

