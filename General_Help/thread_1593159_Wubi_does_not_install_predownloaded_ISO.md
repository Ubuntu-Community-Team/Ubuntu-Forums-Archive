---
title: "Wubi does not install predownloaded ISO"
date: 2010-10-11
forum: General Help
---

### Post by mabarian on 2010-10-11
Hi people, 

I have downloaded Ubuntu (ubuntu-10.10-desktop-i386.iso) and wubi installer for windows, but wubi tries again and again to download an older ISO (10.04) despite the ISO is in the same folder than wubi. 

What's the problem?? Can't see it! I even try to disconnect from internet but doesn't work.

---

### Post by TheAnachron on 2010-10-11
Make sure you mark the "Custom Source" and selected the new iso :)

---

### Post by Mark Phelps on 2010-10-11
According to the latest Release Notes, Ubuntu 10.10 is STILL having installation problems using Wubi.

I would stay away from Wubi for the time being.

---

### Post by bcbc on 2010-10-11
wubi.exe is version specific. They obviously haven't updated the wubi installer to 10.10, perhaps for the reasons Mark mentioned - but more likely just because they haven't got around to it. 
But all images of 10.10 contain the latest wubi.exe.

---

### Post by mabarian on 2010-10-11
Solved problem. I downloaded the correct wubi 10.10 version.

---

### Post by phab8x on 2010-10-11
> **mabarian said:**
> Solved problem. I downloaded the correct wubi 10.10 version.
Hi. Where can i download the correct version of wubi for ubuntu 10.10?
Thanks :D

---

### Post by bcbc on 2010-10-11
> **phab8x said:**
> Hi. Where can i download the correct version of wubi for ubuntu 10.10?
Thanks :D
[http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)

---

### Post by tawfiqh on 2010-10-12
> **TheAnachron said:**
> Make sure you mark the "Custom Source" and selected the new iso :)

How/where does one select custom source?

---

### Post by tawfiqh on 2010-10-13
I got it to work by just putting the iso in the same folder as the new version of wubi, thanks for the link.

---

### Post by Green-Bean on 2010-11-23
> **tawfiqh said:**
> I got it to work by just putting the iso in the same folder as the new version of wubi, thanks for the link.

Putting the ISO file in the same folder as wubi.exe did not work on my Win7 64-bit system.  Perhaps wubi wanted a 64-bit ISO.  However, I burned a CD from the ISO file.  Inserting it launches a self-contained wubi.exe, which ran off the CD, so all's well.

---

