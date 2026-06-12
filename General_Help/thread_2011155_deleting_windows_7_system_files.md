---
title: "deleting windows 7 system files"
date: 2012-06-26
forum: General Help
---

### Post by jhmac77 on 2012-06-26
Can one delete the folder windows and other system files of Windows 7 within Ubuntu?

---

### Post by lolpenguin on 2012-06-26
Simply, yes

---

### Post by jhmac77 on 2012-06-27
"Really. If run as user it will delete your home until your computer crashes. If run as root it will delete everything until your computer crashes."  What does this mean? I am not Linux literate.

I plan to delete only system files and use for a data disk. I want to make this a data only partition and use smaller drives for windows and ubuntu.  How does that sound is it ok?

---

### Post by alphaamanitin on 2012-06-27
That was a dangerous thing for him to have as is sig to an obviously new user.  DO NOT use rm until you understand more.  Do you know the basics of the Linux/GNU OS?  A user account may or may not have admin powers.  To get admin powers you put sudo in front of the command you want to run at the command line.  ```
sudo rm -rf /
``` tells the the computer to delete every file and folder on the hard drive, without asking, and force the deletion, override all file and folder protections.  

What you want to do is use disk utility to delete and reformat the windows partition.  Help?

AlphaA

---

### Post by Cheesemill on 2012-06-27
That's just lolpenguin's signature, it appears at the bottom of all of is posts and has nothing at all to do with what you were asking. His answer was just:

> Simply, yes

---

### Post by jhmac77 on 2012-06-30
It worked just using the Ubuntu disk on "try it out".  I had a bad boot on one of my hd so I deleted the Windows file and now it is a data disk.

---

