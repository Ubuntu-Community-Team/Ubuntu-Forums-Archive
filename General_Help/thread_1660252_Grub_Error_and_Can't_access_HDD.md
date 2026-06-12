---
title: "Grub Error and Can't access HDD"
date: 2011-01-05
forum: General Help
---

### Post by arvin555 on 2011-01-05
I hope someone can help me! My Main goal is to get to important data in the HDD which I hope can be backed up in a USB so I can then reformat and reinstall Ubuntu.

Ubuntu version 9.04 (Jaunty)
Pentium 4 PC Desktop
20gig Hardrive
Dedicated Ubuntu, no dual boot or anything, the HDD is fully for Ubuntu only and partitioned that way. 

1st Problem:
Yesterday I encountered an error while using Ubuntu and OOffice, so I restarted.  Right after the restart I got an error:

GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17

(I checked no USB is plugged in the PC)

So I researched this in the forums, and the suggestions are to boot with a LiveCD and fix.  Unfortunately I have just burned a liveCD now, though I was able to make a liveUSB, and plugged it in.

Problem is that during the boot up of LiveUSB, I encountered another Error:

ata2.01: Status: {DRDY ERR}
ata2.01: error: {UNC}
end_request: I/O error, dev sdb, logical block 8
etc. etc..
This goes on, until the screen just goes blank and no CPU activity.

Above is problem no. 2

At this point I gave up trying to recover Ubuntu, so I'm just in data recovery mode.  My goal as mentioned is to get to the files, back them up and start from scratch.

So I loaded the drive onto a windows XP PC, but the HDD won't get recognized, I went to Device manager, and the HDD is there, but no drive letters.  Dos won't also give it a drive letter.

Okay so I have another PC running Ubuntu, I then installed the "broken" hdd in it hoping to access it through Ubuntu.

During the boot up stage, the DRDY error keeps popping out, but after maybe 20 minutes or so, Ubuntu will be on (same version by the way), BUT, no 2nd drive, it won't get recognized.  the BIOS however does sees it as a secondary slave drive.  It's PATA by the way not SATA. 

I can't do fdsk or e2fsck because the drive is not recognized by the OS or at least not being given a drive letter or anything. 

So now I am unfortunately STUMPED big time.

I hope you guys can give me suggestions on how to fix this, or at the least get me access to the drive so I can backup the files.  

Looking forward to your replies!

TTFN
Arvin

---

### Post by PapaNerd on 2011-01-05
Arvin:

This reply assumes:
1. The working backup machine has either a SATA or PATA drive as the first boot device.
2. There is no conflict in the jumper settings on PATA drives ... boot device should be set to master and the "broken" drive to "slave".

Does the "broken" drive show up when you go into the BIOS?

If the backup machine will boot into ubuntu, either on the primary drive or via CD/DVD, does the "broken" drive show up when you do "fdisk -l" and/or "lshw"?

---

### Post by arunthakurmanali on 2011-01-05
just have look at this link [http://linuxscoop.blogspot.com/2011/01/how-to-fix-grub-errors.html.maybe](http://linuxscoop.blogspot.com/2011/01/how-to-fix-grub-errors.html.maybe) it can help you.

---

### Post by arvin555 on 2011-01-05
PapaNerd,

Thanks for your reply and clarification request.

1. Yes the working Ubuntu PC I used was booting up as primary boot device.

2. Yes I think there is no Conflict, I made sure that the problem HDD is a slave.  Yes it shows up in my Bios as a PATA Slave or something. 

3. I tried fdisk -l unfortunately only the one drive is shown and that is the primary drive, there is no second HDD that is shown by fdisk, I have not tried lshw.

The drive is very frustrating in that, the only thing that detects it is the BIOS, and therefore I cannot do anything to even try to fix it like e2FSCK 

I have a feeling that when I start playing with gparted, that I will already surely lose data on that hDD, right? :(

---

