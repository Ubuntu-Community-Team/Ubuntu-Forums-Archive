---
title: "Recover files via livecd"
date: 2011-09-05
forum: General Help
---

### Post by WikedX on 2011-09-05
LONG STORY SHORT I broke Ubuntu with a kernel update because I can't into video drivers properly. I broke Ubuntu so bad that using the reinstall thing doesnt work from a LiveCD

So I'm trying to copy files over to another hard drive.
A) Ubuntu doesnt see my Windows hard drive now
B) From the LiveCD I can't ****ing copy my files

How do i enable permissions so that a LiveCD can manipulate files in my home folder without going NOT THE USER, ABORT ABORT

---

### Post by WikedX on 2011-09-05
I also want to note how annoying this is that it's locking me out of my own system.

Windows lets me get my files be OBVIOUSLY if I have the hard drive attached to the damn thing... ya know...

If I had "secret" things they'd be encrypted :|

---

### Post by dave01945 on 2011-09-05
have you mounted the windows hdd and have you used sudo to copy the files root can access anyones files

---

### Post by WikedX on 2011-09-05
I used sudo su to become root and copy it that way but nothing.

However sudo su chmod 777 -R ./share worked for me. So solved I guess

---

