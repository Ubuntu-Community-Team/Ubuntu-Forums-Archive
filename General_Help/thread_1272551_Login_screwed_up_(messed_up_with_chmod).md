---
title: "Login screwed up (messed up with chmod)"
date: 2009-09-22
forum: General Help
---

### Post by Moccij on 2009-09-22
Hi!

I've been happily living with Ubuntu 9.04 since I decided to change the permissions of *every* file in my ubuntu partition (from the properties in the "/" file system folder, by accessing nautilus with sudo). I thought life would be easier without open nautilus within sudo in the terminal every time I want to modify something: obviously it was the wrong step to do that.

It loads the login screen, everything seems ok: at the time I entered user & pass I end up with 2 errors. The first complaining about $home/.dmrc and the second says that the session ended in less than 10 seconds. The error log says "etc/profile : 26 : id - permission denied" and some other things.

I've solved the first error by using the chmod 644 method, but I can't figure out how to solve the latter. I've tried the recovery terminal as root, tried to chmod etc/profile but says there's nothing, tried to chmod "/" and succedeed but seems it applies to this folder only.

So: if the mess started by changing all permissions, I think it can be repaired by resetting those permissions right? What should I do next? Thanks in advance!!

---

