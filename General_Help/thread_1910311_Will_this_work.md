---
title: "Will this work"
date: 2012-01-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-01-16
is there a way i can mount a directory (~/Desktop on the /home partition) to the /tmp/$USER-Desktop/ (on the /tmp ram disk partition)
i know i can mount ~/Desktop its own ram disk with fstab but if i can put it in my other (much larger ram disk) it would be better
assuming that is possible what would be the command or would i have to use a symlink?

---

### Post by Joundill on 2012-01-16
I assume your question is whether you can have your /home directory on a separate drive, and the answer is yes.

This link should help.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Joundill

---

### Post by pqwoerituytrueiwoq on 2012-01-16
not quite
i have my /home on its own partition but i also use my desktop for temporary files so i was wondering if i cam use teh mount command to mount my desktop to a folder in my /tmp folder (which is a 6gb ram disk)
currently i am using my desktop as a 0.25Gb ram disk

---

### Post by Xgen on 2012-01-16
If I understand correctly, the location of your Desktop is defined by the ~/.config/user-dirs.dirs file.

---

### Post by pqwoerituytrueiwoq on 2012-01-17
interesting trick but not what i want to do
i was wondering if i could to it with mount the same way i can do a symlink just with no arrow icon telling me it is a symlink

---

### Post by LewisTM on 2012-01-17
It's definitely possible.
The main challenge is that at boot time, /tmp is empty since it comes from plain RAM and doesn't contain a proper directory for your desktop.

Here's what I suggest:
Assuming you have an empty ~/Desktop directory.
Edit your /etc/rc.local file and add the following commands:
```
cp -a /home/youruser/Desktop /tmp
mount --bind /tmp/Desktop /home/youruser/Desktop
```
That should do it. You can test the procedure in a terminal, just add sudo before the mount command.

Cheers!

---

### Post by pqwoerituytrueiwoq on 2012-01-19
thanks

---

