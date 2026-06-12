---
title: "fsck died with exit status 4 - causes?"
date: 2009-07-20
forum: General Help
---

### Post by candtalan on 2009-07-20
A non techie friend has been running ubuntu 8.04.2  on an oldish Toshiba laptop as dual boot, but avoiding Windows, with no problems.

Recently, a lot of USB stick activity was done during one morning  in activity sessions of approximately 30 minutes each, to copy and paste stuff from the windows partition (non wubi) to the ubuntu partition, the partitions are on the same single hard drive. 
I am aware this can be done from within Ubuntu, but the user knows how to use a usb stick, and that is what was used.....

A final action was to notice that a couple of files were in the wastebasket which were not intended to be there, so the user tried to restore them to the original locations, could not see how that could be done, so used the usb stick to copy them out to another location in ubuntu.

The user is a careful and deliberate person and when questioned was sure that on each occasion of usb stick use, the unmount was used, the icon disappearing was awaited, and also the usb stick light going out was also awaited, (although they all were fast).

However, the subsequent problem:

This is how the user reported the subsequent events when the machine was next started up (dual boot default to ubuntu)
=========================
First, I had a message 'Ubuntu couldn't start the X Server (your geographical environment due to some internal error.  Contact administrator or check your syslog to diagnose.   Meantime this display will be disabled.  Please restart GDM when problem is corrected.'

I closed computer down and tried again later.  It then said 'fsck died with exit status 4  . . . run fsck manually'.

I tried once more later on.  It did a routine check of drives, then showed the same message.  
=========================

Comment:
Subsequent to this, the machine has been used sparingly with Windows with Firefox and thunderbird with no obvious problems - same hard drive but different partition.

I will be hopefully repairing the situation soon using the suggested fsck techniques. Backups of data are available ok.

The last action was a usb stick activity from the wastebasket - is there anything special about this which might have caused problems? I guess the wastebasket might be a special file, and usb activity from it might be unusual enough to escape much testing?? 

However, whatever, I am very interested to know possible or likely reasons for this problem to have occurred, any thoughts please, (including about recovery of course)??
tia

---

### Post by afogl001 on 2009-08-18
I had the same problem.  It happened when Wubi Ubuntu locked up in the middle of an update.  I did a hard restart and bam "fsck died with exit status 4"  It's an easy fix though, I believe I did it one of two ways, can't remember which one worked but obviously neither hurt the system.  Either I just type in fsck and hit "y" every time it came across an error (and there were a lot), or I hit "Esc" for menu at boot and selected the second option (numbered 1) which was 9.04 generic (maintenance) or something, then ran the fsck and did the "y" thing.  Hope that helps.

---

