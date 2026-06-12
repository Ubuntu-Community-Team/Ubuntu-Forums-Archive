---
title: "copy/paste from a liveCD of ubuntu"
date: 2011-12-20
forum: General Help
---

### Post by xMusic on 2011-12-20
Hi, 

I have had a problem with a harddrive(windows is corrupted) and it wont load anymore and system restoration won't work either.

So I decided to use a liveCD of ubuntu 10.04

I run it and the harddrive is detected and when I try to transfer my data on my external harddrive, which is like only 8G of data only 1G transfers and I get errors for the rest of the files

[http://i221.photobucket.com/albums/dd161/hieijr/ubuntupb.jpg](http://i221.photobucket.com/albums/dd161/hieijr/ubuntupb.jpg)

anyone know if there's a way to transfer my files anyway?

thanks in advance
xMusic

---

### Post by Mark Phelps on 2011-12-20
If Windows is "corrupted" because, in reality, the filesystem is damaged, then trying to copy files out of it is going to fail somewhere along the line.

If you press the "skip" button, does it continue with other files, or does it stop?

If it continues, about all you can do is keep going and try to copy as many files as you can.

---

### Post by hackb0y294 on 2011-12-20
What Mark Phelps said. You might try a different Live CD distro that's geared toward data recovery, such as the free System Rescue CD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)).

---

### Post by xMusic on 2011-12-21
Yes, when I press skip it continues but in the end i can only get like 1g out of 8g which is really not enough.

I am doing an intership and the person that have had a problem with the harddrive really need to get them back.

:(

---

### Post by coldraven on 2011-12-21
Another option would be to remove the harddrive and plug it into a USB dock.
Then connect it to a Windows machine.
If it shows up as Drive E:
Run   [B]chkdsk e: /r

Also see: [http://en.wikipedia.org/wiki/CHKDSK](http://en.wikipedia.org/wiki/CHKDSK)
[/B]

---

### Post by xMusic on 2011-12-22
I already ran the CHKDSK scan it sees many problems but can't fix anything it seems

---

### Post by xMusic on 2011-12-22
Also the boot from the liveCD System Rescued does not work

edit: I used the liveCD HDD regenerator and apparently despite the fact that it didn't repair all of the bad sectors it made the HDD abble to run in safe mode but verrryyyyy slowly.

After that I transfered my files and now I'm reinstalling the OS

thanks

---

