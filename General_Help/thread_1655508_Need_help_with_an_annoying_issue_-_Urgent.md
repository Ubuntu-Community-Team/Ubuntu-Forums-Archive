---
title: "Need help with an annoying issue - Urgent"
date: 2010-12-29
forum: General Help
---

### Post by TimEnid on 2010-12-29
Seems like everytime i start my pc, i get this annoying issue. its either 1 of 3 things, or all 3 back to back. I turn on my pc and i get this screen
[img]http://lh5.ggpht.com/_HvCNBDIxzvA/TRu2IuF7iAI/AAAAAAAAAA8/EmnZOw42Q_8/s720/2010-12-29_17-19-56_398.jpg[/img]

if its not that screen, its this screen
[img]http://lh3.ggpht.com/_HvCNBDIxzvA/TRu2GA6jvmI/AAAAAAAAAA4/JarhpSSnpFg/s720/2010-12-29_17-12-53_840.jpg[/img]i try typing in my log in, but my keyboard is not responding. sometimes it does, and i type in my log in then it asks me for my password, i put that in and then i just get a blank screen.

and this is the final one
[img]http://lh3.ggpht.com/_HvCNBDIxzvA/TRu2DotJYRI/AAAAAAAAAAU/mNhwYGL-Q5o/s720/2010-12-29_17-22-19_818.jpg[/img]
but the thing about this screen, is that my mouse and keyboard are frozen.
it takes me about 15 minutes to get my pc up and running, after pressing the restart button, the power button or the power supply button. Finally after a few presses, it boots up fine. But i need to remove this issue. If anyone has a solution, can you please provide it. I posted about this issues before, and thought it had went away, but apparently is hasnt.

---

### Post by cariboo on 2010-12-29
After shutting down using the power button have you ever run fsck? To do so boot from the Live CD, and once at the desktop, open a terminal and type:

```
sudo fsck -y /dev/sdXx
```

Where /dev/sdXx is your Ubuntu partition.

---

### Post by TimEnid on 2010-12-30
> **cariboo907 said:**
> After shutting down using the power button have you ever run fsck? To do so boot from the Live CD, and once at the desktop, open a terminal and type:

```
sudo fsck -y /dev/sdXx
```Where /dev/sdXx is your Ubuntu partition.
this is what i get
> ubuntu@ubuntu:~$ sudo fsck -y/dev/sdc
fsck from util-linux-ng 2.17.2
ubuntu@ubuntu:~$ sudo fsck -y /dev/sdc1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sdc1: clean, 336544/29286400 files, 27069925/117145344 blocks

---

### Post by kd5mkv on 2010-12-30
I had alot problems with 10.10, so I used Gparted and reformated the ubuntu partition and re-installed 10.4. My 10.10 stopped dual booting and the grub installer failed to come up on start up!

---

### Post by TimEnid on 2010-12-30
also, in the first pic, where you see [sdm], [sdn] and [sdl], those are my external hard drives? they mount as soon as i boot up. im thinking it has something to do with them.

---

### Post by aeronutt on 2010-12-30
Is this a new install of 10.10?  I remember having a similar issue with 10.04, and it turned out when I ran md5sum on the 10.04 iso, it didn't match....so after I downloaded a complete 10.04 iso, and reloaded, everything worked fine.

---

### Post by TimEnid on 2010-12-30
> **aeronutt said:**
> Is this a new install of 10.10?  I remember having a similar issue with 10.04, and it turned out when I ran md5sum on the 10.04 iso, it didn't match....so after I downloaded a complete 10.04 iso, and reloaded, everything worked fine.

i upgraded from 10.4 to 10.10, i was having the issues with 104 as well.

---

### Post by TimEnid on 2011-01-02
so its been 3 days and the problem has not occured again. i think i may have found the solution. The drives that i mentioned above, are both connected via usb 3.0. I followed the directions found [here]("https://help.ubuntu.com/community/Mount/USB"). Now those drives dont mount at startup and i dont get any freezing issues or the other issues mentioned in my first post. Hopefully this is the solution, just in case anyone runs in to this issue. I will mark this as solved.

---

