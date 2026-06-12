---
title: "Harddrive Failure perhaps? Or a Grub error?"
date: 2011-10-29
forum: General Help
---

### Post by Jdfskitz on 2011-10-29
My original setup is Ubuntu 11.10

Well, I figured my hard drive had plenty of space since the last time I checked it I had at least 110 GB of space.. but, I haven't checked it for a while, and supposedly there is only 1.6 gigabytes of space left, which.. where I am now.. booted in the 11.04 Live CD, (I also tried 11.10), no partitions are detected in the partition manager and I cant find any previous files to delete.
When I perform Sudo fdisk -l , Nothing appears.
but if I dont use a cd, when I try to boot it says No Operating system (if there is a invalid cd in the drive)
and otherwise it will flash and restart at the BIOS screen.

I don't know how many hours I have spent on this. but I would love to be able to fix it. and I have no idea if there is a way, I spent 3 hours searching through files to see if I could do anything. but they are all undetected files.

Please help? any suggestions? I might lose my mind soon..
The thought of taking a sledge hammer to my hard drive is cringing,
I am using an HP Pavillion dv9000 if that is useful in any ways.

the computer janitor comes with up with nothing. the GPartition Manager comes up with nothing, the check disk utility says only 5 gb of space so I cant see where it all is. whereas filesystem just keeps going up in size and saying 1.6 gb remaining, and the install requires 4 gigabytes of space, but I have no way of gaining that.

I can't check my partitions, and I cant find my files... it's like messing with a pissed off chameleon..


(PS: I was browsing around on facebook and downloading ubuntu 8.04 at the time when this happened trying to help my friend fix his ubuntu issue with the mouse drivers in a tablet, kind of backfired.)
--Happened after putting in a cd with no label, that had the series weeds on it, in mkv filetype..

---

### Post by garvinrick4 on 2011-10-29
How many operationg systems on machine and was one windows? Did you by chance
make 5 primarys? What was last thing you were doing before not showing drive.

---

### Post by Jdfskitz on 2011-10-29
I'm not currently using any seperate partitions, just one. Ubuntu, I used to have windows and ubuntu as a dual boot, but I formatted the entire drive for ubuntu. 

last thing I was doing before the drive had the issue??? I was using facebook >.> , closed the window, tried to open up a folder and everything on the screen turned to an error, whereas I had no ability to touch a power button on the screen, no terminal, I couldn't open anything. forcing me to shutdown hard. and then I turned on the laptop, entered my bios password, and the screen flash back to the CMOS before the bios again.

---

### Post by westie457 on 2011-10-29
Hi One course of action that might work is to boot a Live CD in Try mode. Open Gparted and force a check of the file system. It worked for me a while ago.

One question though. Have you deleted a lot of files recently?

If you have and the above suggestion does not work, post back here and we will try something else.

Thank you.

---

### Post by Jdfskitz on 2011-10-29
As I said earlier.. I tried that, thanks for trying to help :\ Nothing appears in the manager.

No, I haven't deleted a lot of files recently..

---

