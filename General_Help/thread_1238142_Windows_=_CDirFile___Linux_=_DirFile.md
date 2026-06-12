---
title: "Windows = C:/Dir/File   Linux = ?/Dir/File"
date: 2009-08-12
forum: General Help
---

### Post by JohnWesleyMethodist on 2009-08-12
Hello,

 I am trying to set up an online game to store the images on my hard drive for faster loading of the game. I downloaded the image pack and gave it a place in my Documents folder.

 In Windows I would type something like: C:/Documents/Games/file

 That doesn't seem to be working in Linux. What do I put in the path instead of C: ?

 I tried C:/home/username/Documents/Games/file but no go.

 Thanx!

---

### Post by P4man on 2009-08-12
In windows, you start with the drive letter (c: in your example). In linux, you dont. everything starts at the root "/". User files will typically be in /home/<your name>/. Its comparable to "my documents" in windows if you like. 

Other hard drives or filesystems can be mounted anywhere, but the usual place is /media/<name of drive>.

Some more info and a nice pic here:
[http://www.linuxconfig.org/Filesystem_Basics](http://www.linuxconfig.org/Filesystem_Basics)

---

### Post by Tibuda on 2009-08-12
There is no 'c:', there is root.

---

### Post by credobyte on 2009-08-12
Here's an example of what equals to what in Linux world ..
```
/ = C:\
/home = C:\Documents and Settings\
```Info: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/the-root-directory.html)

---

### Post by hobo14 on 2009-08-12
Try 

  "/home/username/Documents/Games/file"

---

### Post by HavocXphere on 2009-08-12
> /home = C:\Documents and Settings\
On Vista based OSs its under Users.
C:\Users\HavocXphere

---

