---
title: "Gaining access to a corrupt disk."
date: 2011-12-21
forum: General Help
---

### Post by invertiSm on 2011-12-21
Hi, this is my first post here, and I'm a complete ubuntu noob, so excuse me if this is put in the wrong place.

I'm not actually an ubuntu user; I'm using the liveCD approach to try and gain access to a corrupt disk. The idea was to salvage what could be saved.

However, when I try to access the disk through ubuntu it gives me the following error message:

[I]Error mounting: mount exited with exit code 18:Failed to open hiberfil.sys data attribute: No such file or directory
Failed to mount'/dev/sda3': No such file or directory[/I]

I realize this is not just related to ubuntu only and goes beyond that. However I was told that I might want to try and remove hiberfil.sys to gain access to the disk.

How do I go on about this? Or am I seeing this from a totally wrong perspective? I'd appreciate any help I can get, thank you.

My specs:

Acer eMachines E642
AMD Athlon II X2 p340
ATI Mobility Radeon HD 5650
4GB DDR3

Feel free to ask for any additional information you might need.

---

### Post by jerome1232 on 2011-12-21
Have a look here [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)


If it's your pesonal data on the disk your after, I've had great success with PhotoRec in the past. It can recover your documents, pictures, movies, etc...


Is the disk actually failing or is the file system simply corrupt?


Have you tried running chkdsk from Windows on your disk?
Have you checked the smart data to see if the disk is failing?

---

### Post by invertiSm on 2011-12-21
Thanks for the link! I will follow it and see if it fixes my issue.

Since your questions asks for it, I'll give the full rundown on the situation: (which I should've done in the first post.)

My laptop, out of nowhere, gave me a bluescreen at boot with the following information:

DRIVER_IRQL_NOT_LESS_OR_EQUAL
STOP: 0x0000007E (0xFFFFFFFFC0000005,
0xFFFFF800131F30F3,
0xFFFFF880009A87D8,
0xFFFFF880009A8030

I've already asked around on other forums what this means so I don't expect an explanation here. What happened after this was that I could not boot windows whatever the case: repair, safemode etc. nothing worked, it crashed and gave me a bluescreen every single time. At repair it would read in files until it reached "atipcie.sys", stopped, bluescreen etc.

I had not installed or updated anything prior to this. The previous file I mentioned in my first post, hiberfil.sys, made me consider the fact that I might've turned the laptop off incorrectly during hibernation or something to that effect. I can't be 100% sure on this one.

SPECS:
Acer emachines E462G
AMD Athlon II X2 P340
4GB DDR3
ATI Mobility Radeon HD5650
Windows 7 64-bit Home/basic whatever it's called

I was given the tip to try ubuntu livecd and recover my files through it. As you probably realize I have no idea what the actual failure within my pc is. Also, I have two 2GB memory sticks and I tried booting with only one and each. My laptop won't boot with one of them. At first I thought this was the only issue, but when I boot with only the memory that works, I still get the error message posted in my first post. My point is that I sadly can't tell you what is failing; the file system or the harddrive itself. Yes, it's the one and only drive on the computer.

Continuing on that, I can't check smart data/chkdsk since I can't access Windows at all. If there is any other way to do this, please let me know.

Finally, thanks for recommending Photorec. I've no idea how I'll use it without access to Windows. If nothing else works, I'll remove the HDD and recover the files on my stationary or something.

---

### Post by jerome1232 on 2011-12-21
To check Smart data from within Ubuntu you can click on the Ubuntu logo at the top left of your screen, search for "Disk Utility", pop that open.

Select your disk in the left hand pane, on the right hand side click "View Smart Data" Here you can see the data if the disk is failing, you can run a test if you need to as well.

-----------------------------------

If the disk is failing you need to get your personal data off pronto and buy a new disk. Now it's possible the file system is just corrupted from those blue screens, I would recomend running chkdsk from a Windows recovery disk.

I actually have to run to work like right now, I can post more later.

edit: Photorec can be used from a live cd, but you need another disc to write the data it recovers to.

---

### Post by invertiSm on 2011-12-22
Yeah, I'll probably need to get an external in any case.

Running CHKDSK as im typing this. Had to do it through command prompt, with the help of Hiren's boot CD. (mini xp.)

After this I'll check the smart data and - when I get my external drive - try testdisk/photorec. HDDregenerator was also recommended on some other site, I believe it's also on Hiren's boot CD.

I'll post my results later.

---

### Post by invertiSm on 2011-12-22
Ok, ran check disk through mini xp (with the help of hiren's boot cd), took about 4 hours to run through everything. Said it couldn't catch a log for it, whatever. Tried accessing the disk, worked. Rebooted with my normal Windows 7 64-bit - now with 2GB less memory - runs fine with no problems at all.

Glanced through what was most important and most of it seems to be intact. I'll be sure to backup this time.

Thanks a million jerome, I really appreciate it especially considering neither help nor solution ended up being ubuntu-related.

I'll leave the thread for a bit, and close it later on unless someone else or you have anything else to say or contribute. Again, thanks!

---

### Post by jerome1232 on 2011-12-23
I'm glad to hear your data was intact, I would double check smart just to make sure you disk is fine (sounds like it is)

You should give Ubuntu a try sometime as a Wubi install (it's an easy way to test drive Ubuntu without actually partitioning your disk up) It's a great OS!

One piece of Open Source Software I like for backups is Clonezilla, it's similar in function to Norton Ghost, it can make a compressed image of your entire drive so you can just restore your entire system to the time you made the image, I like to do these full images every 6 months and just backup my personal data every month in the interim. You would need an external drive to do this kind of backup though. It's a bit intimidating your first time using so I'd recommend reading a guide if you try it out.

---

### Post by dargaud on 2011-12-23
I recommend PhotoRec too. I use it regularly on my cameras SD cards when my wife complains: "There was this photo I remember seeing on the camera, but I don't see on the PC..." "I deleted it because it was out of focus/badly framed/..." "I want it because..."

---

### Post by invertiSm on 2011-12-23
Haha, I'm not married yet but I sure recognize that from girlfriends/family. And when you don't find what they want... you'll never hear the end of it.

I'm actually running Win7 on my stationary and Ubuntu on my laptop now. (I backed up school/work stuff and reformated.) I liked the interface/design so much I decided to give it a try, plus my friend had spoken very good of it previously. If you don't mind me asking, what are the reasons you guys run Ubuntu? If you were to pitch it. I'd like to hear some more "mainstream" reasons for it.

Off to ordering an external!

---

### Post by jerome1232 on 2011-12-24
[LIST=1]
[*]The Community
[*]The Package Manager
[*]Enhanced Security
[*]Flexibility
[*]The Open Source Concept
[/LIST]

---

