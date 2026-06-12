---
title: "Serious issues with booting Ubuntu!"
date: 2011-11-18
forum: General Help
---

### Post by insanekat on 2011-11-18
Running Ubuntu 11.10 (and dual booting Windows 7).

So I went out last night and turned off my computer, which was running perfectly normally, then came back and went to boot it up but it went to the blank screen with the little white cursor. Tried running other versions with the same results. Went back and ran it in recovery mode, did the fdisk check, it ran through a lot of error messages then told me to hit enter, which I did. Went to repair broken packages, it also ran through a lot of error messages, but still got to the hit enter part. Went to resume normal boot, it ran through even MORE error messages then went to a blank screen. I tried this with various versions in various orders with the same eventual result of a blank screen. 

There were a lot of repeated error messages (if someone can tell me how to get a read out of these that would be helpful! I can access my files on Ubuntu through Windows 7). But what I could get down is the following:

```
ata1.00: status: {DRDY ERR}
ata1.00: error: {UNC}
ata1.00: configured for UDMA/100
ata1.00: EH complete
```
This repeated a lot.

Also,
```
Buffer I/O error on device sda6, sector 35092708
```
This repeated also, and had it with sda8 as well.

I know my lack of information right now is probably very unhelpful but I hope I'm not screwed, so any help would be appreciated!

---

### Post by jonnyboysmithy on 2011-11-18
I would think some part of your hardware might be dying..:-&

---

### Post by insanekat on 2011-11-18
That sounds bad, why would that happen? This computer isn't even a year old...

---

### Post by jonnyboysmithy on 2011-11-18
You could make a livecd or liveusb and run some disk checks to see if your harddrive is intact.
Maybe bad memory? There is also a memory test on the live systems.
It could be anything really like too little power to some part of your motherboard or harddrive, but I would start by checking the harddrive..
Also I used to get I/O errors when my laptop ran to hot.

Hope that helps;)

---

### Post by jonnyboysmithy on 2011-11-18
> **insanekat said:**
> That sounds bad, why would that happen? This computer isn't even a year old...
Lol for that matter I've heard of a 4 week old hardrive that broke down, I've had a few that also just slowly got lots of error. It happens, stuff fails. Keeping backups also helps. Start with getting a liveusb/livecd and using disk utility to see whether your disk is failing.
btw I'm assuming you don't have a SSD harddrive?
EDIT:Its getting rather late in my time zone I'll be back tomorrow :)

---

### Post by sapnewbie on 2011-11-18
Try to scan for defects using ddrescue. [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by jonnyboysmithy on 2011-11-18
you might want to have a look at [http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by insanekat on 2011-11-18
Ah okay, would just doing a fresh install of Ubuntu on it work? 

I ran the memtest but it showed no errors.

---

### Post by insanekat on 2011-11-18
> **sapnewbie said:**
> Try to scan for defects using ddrescue. [http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)
Probably a dumb question but... How do I do this on the Windows machine...?

---

### Post by jonnyboysmithy on 2011-11-18
> **insanekat said:**
> Ah okay, would just doing a fresh install of Ubuntu on it work? 

I ran the memtest but it showed no errors.  Do you have a separate home partition? If you do it makes things a little easier. [http://ubuntuforums.org/showthread.php?t=1854501](http://ubuntuforums.org/showthread.php?t=1854501)

---

### Post by insanekat on 2011-11-18
> **jonnyboysmithy said:**
> Do you have a separate home partition? If you do it makes things a little easier. [http://ubuntuforums.org/showthread.php?t=1854501](http://ubuntuforums.org/showthread.php?t=1854501)
Yes, I do, thank you!

---

### Post by jonnyboysmithy on 2011-11-18
> **insanekat said:**
> Probably a dumb question but... How do I do this on the Windows machine...?(I'm assuming that you want to install ddrescue on windows)
First you would have to find an emulator to run the program inside of windows, then install more stuff so it can read ext partitions, (if windows gets a virus it will have the ability to infect the ubuntu drive, it won't affect ubuntu but then you have that to deal with that), and why do that when you can just use a livecd to run the software natively? Ok you could do it but to me it seems easier to just use a livecd.:popcorn:

---

### Post by jonnyboysmithy on 2011-11-18
> **insanekat said:**
> Yes, I do, thank you!
Great! If you want to reinstall why not?
You are familiar with how to preserve the home partition I hope, because its nice when you don't accidentally delete all your stuff.:p

---

### Post by jonnyboysmithy on 2011-11-18
I wonder why it got all those errors to start with...

---

### Post by insanekat on 2011-11-18
Does it explain how to in that thread? I haven't done it before, so... A step by step would probably help me. I just don't have time to deal with it right now so I'll actually try it later.

Haha I would also like to know what happened!

---

### Post by jonnyboysmithy on 2011-11-18
I if you run the installer you have the option to reinstall ubuntu and preserve the home folder:

---

### Post by insanekat on 2011-11-20
Okay duh! I should be fine then. Thanks for the help guys, hopefully it will be all good.

---

