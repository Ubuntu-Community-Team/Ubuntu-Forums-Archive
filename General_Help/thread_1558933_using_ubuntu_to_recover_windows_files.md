---
title: "using ubuntu to recover windows files"
date: 2010-08-22
forum: General Help
---

### Post by fuzzypumpkins on 2010-08-22
i have windows xp on my little laptop here and i decided to test run 10.04 ubuntu. Everything was great and i was exploring ubuntus menus and everything. i decided i wanted to install it and have winxp and ubuntu dual booting. so i started installing it and got to the partition section. I wasnt real familiar with that setup so i closed it down and was going to try and setup the partitions in windows because i was used to that. i dont know what happened, but when i tried to get into the recovery console on windows, it just started formatting my pc....it was the ghost console or whatever its called. And it started formatting about 2-3% and nothing would stop it so i manually shut down the pc. now when i boot it up i can go to the bios or wait a few seconds and it will just have a black screen with flashing cursor in the top left. So i went into the bios and made my ubuntu boot first and it works fine still, now i am typing on it. I used some commands in terminal to basically see what my partitions still have left. I only really want the photos and some other files on the partitions. i can see the 'documents and settings' folder in the terminal but im not sure how to go about getting files from it. Gparted shows like 28gb of used space so there are files still there. Going into the filesystem also shows the documents and settings folder but says it is empty.

any help would be nice, just let me know if you need to know anything else about what i tried already.

---

### Post by BigCityCat on 2010-08-22
Open your file browser and on the left the windows file system should be located there. It should say a number and GB File System. Navigate through your windows file system and copy and paste everything you want to save.

---

### Post by Rubi1200 on 2010-08-22
Hi and welcome to the forums :-)

There are a couple of options you can try:

1. Use a live distro called Knoppix to try and recover the files:

[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

2. Take a look at the options here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Meantime, do NOT try and write anything to the partition.

Hope this helps.

---

### Post by fuzzypumpkins on 2010-08-22
well i think im screwed then, because i looked at the side bar, and it shows two partitions, they both open up.  The first one has the documents and settings folder that i want to access.  The only problem is when i open that folder it is empty.  Gparted tells me that there is 26gb or so of used space.  I know when i had to do recover files before using windows, i just used a program and i could access the deleted files.  Is there anything like that for linux?...something i could install and use to get to my files that may have been damaged?

and would i even need to use knoppix if i have a fully working ubuntu on a usb stick?

---

### Post by oleink on 2010-08-22
> **fuzzypumpkins said:**
> well i think im screwed then, because i looked at the side bar, and it shows two partitions, they both open up.  The first one has the documents and settings folder that i want to access.  The only problem is when i open that folder it is empty.  Gparted tells me that there is 26gb or so of used space.  I know when i had to do recover files before using windows, i just used a program and i could access the deleted files.  Is there anything like that for linux?...something i could install and use to get to my files that may have been damaged?

and would i even need to use knoppix if i have a fully working ubuntu on a usb stick?

testdisk and photorec

---

### Post by fuzzypumpkins on 2010-08-22
i will check them out, thanks

---

### Post by oleink on 2010-08-22
> **fuzzypumpkins said:**
> i will check them out, thanks

No problem.  Hope it's helpful.  It can often even recover deleted files (don't ask me how) but I was able to recover several gigs of pics on an external hard drive that got deleted.  And testdisk is kind of misleading in its description because apparently it works for more tasks than it says?  (correct me if im wrong)



Also check**
[http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html]("http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html")

---

### Post by fuzzypumpkins on 2010-08-22
yeah i was looking at it before and i kinda passed over it because it didnt look like what i needed.... so i am gonna try it in a bit.

i also just found this video which looks like exactly what i need, im gonna post it in case anyone else has the same trouble i am in.

[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

im just hoping it will recover my windows files and be able to boot back into windows when its finished.

---

### Post by oleink on 2010-08-22
> **fuzzypumpkins said:**
> yeah i was looking at it before and i kinda passed over it because it didnt look like what i needed.... so i am gonna try it in a bit.

i also just found this video which looks like exactly what i need, im gonna post it in case anyone else has the same trouble i am in.

[http://www.youtube.com/watch?v=EncqYP1ijFg](http://www.youtube.com/watch?v=EncqYP1ijFg)

im just hoping it will recover my windows files and be able to boot back into windows when its finished.

Yeah idk if it will be bootable to it afterword... That'll be either a hit or miss probably.... BUT it should recover AT LEAST some files

---

### Post by fuzzypumpkins on 2010-08-22
well testdisk found a partition and supposedly recovered it, then i had to reboot.

after the reboot, i cannot boot from my usb anymore, it isnt even in the list to boot from.  So now I possibly have my files but i can't get into an operating system to see if they are there.


...i should have just done photorec first while i still had a working ubuntu.  :(

then at least i could have seen the files it found (if any).

---

### Post by oleink on 2010-08-24
> **fuzzypumpkins said:**
> well testdisk found a partition and supposedly recovered it, then i had to reboot.

after the reboot, i cannot boot from my usb anymore, it isnt even in the list to boot from.  So now I possibly have my files but i can't get into an operating system to see if they are there.


...i should have just done photorec first while i still had a working ubuntu.  :(

then at least i could have seen the files it found (if any).

Wait it isn't in the list on the bios?

---

### Post by fuzzypumpkins on 2010-08-24
Yeah my usb drive wasn't showing up, but after many restarts it showed and I could boot from it.  Ubuntu worked again but nothing I could do got my files back. So I plugged in the hdd into my other desktop to see if that might work.  I was able to finally find a program called Art Plus Digital Photo Recovery that got all my stuff back.  Only problem was I had to pay for it in the end.  Then I wiped the hdd clean and installed 10.04.  Done and done.

---

### Post by oleink on 2010-08-25
> **fuzzypumpkins said:**
> Yeah my usb drive wasn't showing up, but after many restarts it showed and I could boot from it.  Ubuntu worked again but nothing I could do got my files back. So I plugged in the hdd into my other desktop to see if that might work.  I was able to finally find a program called Art Plus Digital Photo Recovery that got all my stuff back.  Only problem was I had to pay for it in the end.  Then I wiped the hdd clean and installed 10.04.  Done and done.

Alright well glad you figured something out.  I'm really suprised testdisk didn't work for you.. Did your hard drive show up as just the hard drive or did it also show up as a disk (like cd) because it did for me when I did it and doing the hard drive did nothing but doing the cd worked.  It recognized it as a cd because it only looked at used space

---

### Post by fuzzypumpkins on 2010-08-25
It saw it as a hdd with only a couple folders in it.  The folders were empty though.  It's weird that all of the programs I tried showed no useful results.  Then I use a program for digital cameras and it worked perfectly even though I didn't have a digital camera connected.

---

### Post by oleink on 2010-08-25
> **fuzzypumpkins said:**
> It saw it as a hdd with only a couple folders in it.  The folders were empty though.  It's weird that all of the programs I tried showed no useful results.  Then I use a program for digital cameras and it worked perfectly even though I didn't have a digital camera connected.

I see haha yes very strange :)  Glad it worked out though

---

