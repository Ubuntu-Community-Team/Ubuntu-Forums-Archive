---
title: "Ubuntu Installation Error"
date: 2011-06-16
forum: General Help
---

### Post by hirankb on 2011-06-16
Hi,
 
When trying to install Ubuntu (also tried Kubuntu) onto my pc (Intel core 2 duo) inside Windows XP, the following error occurs:
Invalid tag data. Check len(d)=1, (ord(d) & 12==128. Received->(<)
 
Anyone know how to fix this problem?
Thanks!

---

### Post by Rubi1200 on 2011-06-16
Hi and welcome to the forums :-)

The first thing to try is download the wubi.exe and relevant Desktop ISO image and place them in the same folder. Then run the executable file:


> For 10.04 use [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/) 

For 10.10 use [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/) 

For 11.04 use [http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
If this doesn't fix the problem, then do the following:

right-click Wubi.exe and select "Create Shortcut". Then right-click the  shortcut, select Properties, and modify the Target line, for example: 
"C:\Documents and Settings\<user>\Desktop\wubi.exe" --skipmd5check

---

