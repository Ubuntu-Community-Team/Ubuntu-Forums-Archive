---
title: "Need help backing up my home directory"
date: 2009-11-22
forum: General Help
---

### Post by recentconvert on 2009-11-22
I want a way to backup my home directory without compressing anything or creating links. 
I don't mind stashing everything in a container file as long as nothing gets compressed.

---

### Post by mo.reina on 2009-11-22
cp -r ~/ *destination*

---

### Post by recentconvert on 2009-11-22
> **mo.reina said:**
> cp -r ~/ *destination*

I thought that created links, I'm trying to avoid links.

---

### Post by mo.reina on 2009-11-22
cp will **copy** files and directories.  this is what you're looking for right?  backing up without compressing is basically just brute force copying, or are you looking for something else?

---

### Post by recentconvert on 2009-11-22
Yes I was looking for a way to copy without making links or stash in a container without compression. Thanks for the help.

---

### Post by warfacegod on 2009-11-22
Why not simply use your file browser to copy your home folder to another location?

---

### Post by recentconvert on 2009-11-22
> **warfacegod said:**
> Why not simply use your file browser to copy your home folder to another location?
That method creates links instead of copying everything. Which is what I'm trying to avoid.

---

### Post by scouser73 on 2009-11-22
For backing up I use [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html"), the tutorial shows you how to use it and in my opinion I think it's an excellent program for backing up data.

---

