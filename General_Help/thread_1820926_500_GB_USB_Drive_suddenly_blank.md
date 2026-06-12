---
title: "500 GB USB Drive suddenly blank"
date: 2011-08-08
forum: General Help
---

### Post by jatwood on 2011-08-08
Hello everyone,

First, I wanted to say thanks to the all of the people who have posted help tips in the past; as I've undoubtedly had to use them before (usually with great success).

I'll try to keep this as clear and concise as possible:

I've been using Ubuntu for nearly a year now and I've always had an external USB drive (Western Digital 500 GB) connected.  I only used the USB drive to back up files when needed, by dragging and dropping files onto the drive. Anyway, a few days ago my screensaver wouldn't wake from mouse or keyboard input, so I had to shutdown by pressing the power button on my computer. I also manually removed the USB plug without unmounting. (yes, I know I shouldn't have done this). Upon restarting and mounting the USB drive, everything on my USB drive was blank. I checked the hidden files and folders and couldn't see any of my data. I had about 150 GB of pictures, music, documents and spreadsheets. I tried using Photorec, but surprising it found mainly .mp3 and about 10,000 .txt files, and it found zero picture files. The .txt files contained a bunch of special characters/symbols sometimes, and other text that wasn't really relevant to what I was trying to find.

I'm at a loss right now. Should I try Testdisk or take it to a professional?

I know that it was sloppy of me to always have the USB connected, but I would still like to get my picture and document files back. 

I tried searching other threads, but none were specific to this situation.

I'm using 10.04, with a separate /home partition.

---

### Post by Basher101 on 2011-08-08
As far as i know, youre lost pal. Taking to "professionals" is not a great idea...unless your pictures mean death if lost. Those professionals will ask for a few thousand bucks..

---

### Post by JASONFUSARO on 2011-08-08
I am not an expert but I would give testdisk a try but be very careful about selecting any save options just run it and you may have success, it has worked for me JUST BE VERY CAREFUL ABOUT SAVING ANYTHING running it will locate what is there if in fact it is there, then read on how to recover.

BEING CAREFULL I CAN't STRESS ENOUGH, I messed up with photorec you have to watch where that is saved to but as I said I have had success with testdisk


BE CAREFUL

---

### Post by psusi on 2011-08-08
What filesystem is the drive using?  If it is NTFS, you should have windows scandisk it.

---

### Post by JASONFUSARO on 2011-08-08
> **psusi said:**
> What filesystem is the drive using?  If it is NTFS, you should have windows scandisk it.


No usually NTFS, just let it run, may take awhile but let it finish, if you have not used it before read up on the options, just watch the save MBR etc..  don't do any of that, it will find what is there, mine was major messed up overwrote with an install, luckily I caught it before I kept doing any writing.


You might even practice on a USB or something, delete the stuf that is there and then practice with that to get the command options figured out so you can be on top of it.



EDIT**********


AGAIN BE CAREFULL!!!!


ALSO I am new to Linux myself but I like breaking things and trying to fix them, but you may not, and just bide your time and someone more experienced than myself will spot this thread and better advice will come your way, don't do anything drastic to complicate things though, leave as much unchanged as possible, recovery will be simpler that way if at all possible, which it usally is if an expert can do it there are experts here and they won't cost you.

---

### Post by jatwood on 2011-08-08
> **psusi said:**
> What filesystem is the drive using?  If it is NTFS, you should have windows scandisk it.

Hi, it's a FAT32 file system. As I mentioned above, I was able recover a ton of files (mostly .txt gibberish) and some .mp3, but no picture or documents.

Also, I was very careful not re-write anything to the external USB, because I know that it may make recovery impossible.

I may give testdisk a try.

---

### Post by JASONFUSARO on 2011-08-08
> **jatwood said:**
> Hi, it's a FAT32 file system. As I mentioned above, I was able recover a ton of files (mostly .txt gibberish) and some .mp3, but no picture or documents.

Also, I was very careful not re-write anything to the external USB, because I know that it may make recovery impossible.

I may give testdisk a try.

I EDITED my last post I don't know if you re-read it?

---

### Post by jatwood on 2011-08-08
> **JASONFUSARO said:**
> I EDITED my last post I don't know if you re-read it?

Yes, I just read your reply. I'll try to be as patient as possible.

What kills me is how easy it was for me to erase all of my data. We all make mistakes, and simply unplugging the USB cable shouldn't have caused such a catastrophe. There really ought to be a fail safe for these USB devices.

---

### Post by psusi on 2011-08-08
> **JASONFUSARO said:**
> No usually NTFS, just let it run, may take awhile but let it finish, if you have not used it before read up on the options, just watch the save MBR etc..  don't do any of that, it will find what is there, mine was major messed up overwrote with an install, luckily I caught it before I kept doing any writing.

You seem to have started typing in mid thought and left out important context required to understand what you are saying.

> **jatwood said:**
> Hi, it's a FAT32 file system. As I mentioned above, I was able recover a ton of files (mostly .txt gibberish) and some .mp3, but no picture or documents.


After a dirty shutdown, FAT32 needs a scandisk / fsck to recover.

---

### Post by jatwood on 2011-08-09
Well, I tried using testdisk last night, and couldn't recover anything. It took about 1 hour to scan the the entire disk. I downloaded scalpel and foremost too but haven't used them yet.

I'll have to read about commands for scalpel since there isn't a GUI or graphical interface. If anyone has any other suggestions please let me know.

---

### Post by psusi on 2011-08-09
Again, fsck / scandisk it.  testdisk is for recovering broken partition tables, you probably just have a damaged filesystem that needs a fsck, as fat32 ALWAYS does after an unclean shutdown due to not having a journal.

---

### Post by JASONFUSARO on 2011-08-09
> **psusi said:**
> You seem to have started typing in mid thought and left out important context required to understand what you are saying.



After a dirty shutdown, FAT32 needs a scandisk / fsck to recover.



Post #5 was an inadvertent quote tag, the post was intended for the OP, I should have looked it over a little more closely, I thought I had quote tagged the OP's post. 

I apologize for the mishap! I have to be more mindful, and as per your input more concise, thank you for the input psusi.

---

### Post by jatwood on 2011-08-10
I tried using fsck through CLI and the Graphical Interface with Disk Utility in ubuntu, and still couldn't see any of my files.

This morning I used the chkdsk command in Windows; still nothing.

The only files/directories that are on the drive (since this happened) are the:

.trashes
.spotlight-V100
.fseventsd
._.trashes

I don't really know what else I can do except use something like foremost. I have learned something though.... I won't ever be using an external USB drive anymore for storing large amounts of data. What a waste.

---

### Post by psusi on 2011-08-10
> **jatwood said:**
> I don't really know what else I can do except use something like foremost. I have learned something though.... I won't ever be using an external USB drive anymore for storing large amounts of data. What a waste.

That's the wrong lesson here.  The correct lessons are:

1)  Always unmount and safely remove devices before pulling the plug
2)  Use a more reliable filesystem than FAT32, like ext4.

---

### Post by jatwood on 2011-08-10
> **psusi said:**
> That's the wrong lesson here.  The correct lessons are:

1)  Always unmount and safely remove devices before pulling the plug


I agree with unmounting; however, we all know that "safely ejecting" is not always possible when your OS is unresponsive. How are you supposed to unmount when ubuntu suddenly doesn't work?

It shouldn't be this easy to destroy data, plain and simple. I can understand if I were performing a read/write operation to the drive, and then unplugged it, but I wasn't...it was simply plugged in. 

I read that FAT was a primitive file system (although ubiquitous) in the USB world. I'll switch to something more up-to-date for removable hard drives.

Thanks to everyone who responded.

---

### Post by oldfred on 2011-08-10
I agree with using a better file system. 

To shutdown you should at least try raising elephants first.:)

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

or:

Generally pressing and holding Ctrl+Alt and
then PrintScr, R, E, I, S, U, B (Raising Elephants Is So Utterly Boring)
should do a clean reboot.
R gives back control of the keyboard, S issues a sync, E sends all processes but init the term singal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

---

### Post by FerroPower on 2011-08-10
_Off-Topic _: I am using WD 250 GB external disk for storing all my files, I have ubuntu 11.04 working in that disk plus there two NTFS partitions on that disk. Kubuntu 11.04 & win 7 is installed on my laptop. I have never lost any data nevermind how many times i have done shutdown due to some kubuntu app or wine program. my external hard disk is working fine and perfect, no bad sector or any file lost. 

After hearing your case I am thinking of getting a backup of my HardDisk. And thanks to oldfred for teaching raising skinny elephants.

---

