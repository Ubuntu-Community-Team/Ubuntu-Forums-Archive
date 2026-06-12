---
title: "Boot Problem."
date: 2010-01-27
forum: General Help
---

### Post by Haroldsoto on 2010-01-27
Hey guys, i'm kind of new to Linux, and i think i did something wrong x.x. Before i got this error, i uninstalled the Python v2.6 because i needed the v3.1 for a class. But now, when i turn on the Laptop, it says Grub Loading, ok, but then, the screens stays black and with two underscores over the right top... something really weird. Now in running on a live session. But the fact is, that i dont wanna lose all the important data i got. On the live session, in places, i see the 250Gb filesystem. I can see the home folder, but i cant see the photos, docs, etc. they seem restricted. Is there any way to copy those files from a live session to a external HDD? 

Really need help on this. Wanna recover the files. Thanks in advance.

---

### Post by audiomick on 2010-01-27
Hallo.
There was a thread about a day ago from a guy who did much the same. Have a read and see if you can find some help there.
[http://ubuntuforums.org/showthread.php?t=1390910](http://ubuntuforums.org/showthread.php?t=1390910)

As far as your files go, if you start the file manager with
```
gksu nautilus
```
you should be able to see and move anything.
"gksu" gives you root privileges. You would normally be asked for a password, but in the live cd you wont.

---

### Post by Haroldsoto on 2010-01-27
Wow, thanks. Now i can copy the files :D. Gonna back'em up and reformat :s

---

### Post by audiomick on 2010-01-27
If you re-install, think about making a seperate partition for /home. That way, if you have something similar again, you will be able to just re-mount the existing home partition during a re-install, thereby retaining all your data and settings.

---

### Post by Haroldsoto on 2010-01-27
Ok, thanks. But could you give me more info bout that? xD' im kind of noob using Ubuntu. How much space should i put to the partitions?. So, one for /home/ and one for the Ubuntu files and so? How much Swap do i need to put in? (the laptop has 3gb Ram)

---

### Post by audiomick on 2010-01-27
here is some info:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I do this:

partition for / between 10 - 15 GB

this is where the system is. It will have about 2.8GB in it after a fresh install, but it grows. Mine has about 6 GB in it now, after a couple of years of updates and a fair bit of installing anything that caught my interest. If your HD is not very large, go for 10GB.

swap partition a tiny bit bigger than your RAM if you want hibernate to work. If hibernate is not an issue, about 1GB is enough for most people.

partition for /home with the rest of the space.

I am going to bed now. I will look back in tomorrow. Good luck.

---

