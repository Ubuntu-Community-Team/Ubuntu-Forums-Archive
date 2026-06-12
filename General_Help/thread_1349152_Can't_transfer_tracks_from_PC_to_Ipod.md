---
title: "Can't transfer tracks from PC to Ipod"
date: 2009-12-08
forum: General Help
---

### Post by Smokin.Jo.mAmA on 2009-12-08
Hi I am new to the forums and new to ubuntu.

I have an Asus eeepc 901 with 2GB of RAM. I just formatted my XP and installed Ubuntu UNR 9.10. I realize it is not that hard to use, it is well built as far as I can tell, and it responds faster than the XP that shipped with my net book.

My problem is that I have an Ipod classic 120GB that I bought last January. I am using the rhythm box that comes with the OS. The Ipod syncs with Ubuntu no problem, and I can transfer mp3's from the Ipod to the netbook, but I can't transfer mp3's to the Ipod for some reason. Any ideas?

Before Ubuntu I was using sharepod since itunes lags my PC. Sharepod was fairly simple to use and was fast. What I liked about it is that I can leave the ".exe" file inside the Ipod and I can manage my music on any computer even if it does not have itunes. Now I am wondering if the ".exe" has anything to do with me not being able to transfer music from the PC to the Ipod, but I doubt that is the case.

Anyway, the error message I get is:
**Error Transferring Track**
Error opening file '/media/Apod/ipod_control/Music/F46/9h-Roxette- It Must've ~YC.mp3': Permission denied

Any helpful suggestions?

---

### Post by Vishnu V on 2009-12-08
this means that your Ipod get mounted as read only.
Press Alt + F2 and enter gksudo nautilus it will open nautilus in super user mode now you can transfer music.

---

