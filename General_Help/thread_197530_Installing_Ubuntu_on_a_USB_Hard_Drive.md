---
title: "Installing Ubuntu on a USB Hard Drive"
date: 2006-06-15
forum: General Help
---

### Post by essjay612 on 2006-06-15
Ok...this post might get a little lengthy, but I want to be as thorough as possible.  

I have an eMachines WD3400 desktop PC.  Currently I have three hard drives:  

hda:  Windows XP Home
hdb:  Ubuntu Dapper
sda:  NTFS Seagate 160GB USB HDD

When I installed Ubuntu on my hdb, I also installed GRUB on hdb.  Then I made an image of the boot sector using bootpart, and saved it to my Windows drive.  Bootpart also modified my boot.ini file to give me the Linux option at startup.  I have to leave the Windows drive (hda) untouched, and I must keep Windows XP because I go to school online, and that's one of the requirements.  My set up now works beautifully; all my hardware is recognized in Ubuntu, the dual boot runs perfectly...everything is sweet. 

But now my hdb, that currently runs Ubuntu, is making funny noises and I fear it's going out on me.  I can't really afford to buy a new internal drive, and I have that 160Gb of space on sda just waiting to be used.  So here's my idea:

Partition the sda external drive into two halves:  one half for Windows XP storage, the other for Ubuntu.  As I said before, I need to install GRUB on the sda drive, as I don't want to mess with the hda (Windows) drive.  

But my PC does not boot from a USB device.  So my question is this:  How can I install Ubuntu on my external USB drive (sda), along with GRUB, and use NTLDR to pass control to GRUB when I select that option at start up?  Will the PC boot that way, even though the BIOS doesn't support USB booting?  Or will I need to make a boot CD?

I'm almost out of the newbie stage with Linux; I know some of the basics, but I'm no expert.  So any help would be great, but please try not to get too technical on me.  :))))

Thanks in advance.  :))

---

### Post by yager on 2006-06-15
DaBrugo has been the keeper of a great thread on external USB drives.  Many users in the thread have worked through the same issues.
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)
Basically you may need to set up a CD or floppy with GRUB to handle the problem of not being able to boot from USB.

You may want to check if there is an upgrade available on your BIOS.  I had an issue originally and patched the BIOS.  That removed all of my barriers.  Just a thought before you get in to the main thread.

---

### Post by essjay612 on 2006-06-16
Thanks for the tip!  Sadly, that tutorial mentions setting the USB drive in the boot order, and my PC won't boot from a USB device.  It doesn't show up in the BIOS at all.  

Is there a way to make a cd to do this for me?  I only boot my PC once a day, so a CD really isn't inconvenient.  :))  Unless there's another way....?  :))

Thanks again.

---

### Post by yager on 2006-06-16
[QUOTE=essjay612]
Is there a way to make a cd to do this for me?  I only boot my PC once a day, so a CD really isn't inconvenient.  :))  Unless there's another way....?  :))

Thanks again.[/QUOTE]

Read in to the responses.  There are several individuals who add to the discussion about half way in to address the use of a boot floppy and a CD method for booting with GRUB to the USB device.  It gets a little long in some places with all the Q&A but it is in there.  Zerlinna provided a link at this location.
[http://www.ubuntuforums.org/showpost.php?p=865194&postcount=334](http://www.ubuntuforums.org/showpost.php?p=865194&postcount=334)

This is the 334th message in the thread.

---

### Post by essjay612 on 2006-06-16
Thanks!  And sorry...I didn't realize there were that many posts.  LOL.  I'm new to this forum, and it's set up a little differently than what I'm used to.

I'll check that link out and hopefully will figure something out.  :)  Thanks again, and sorry for the n00b questions.  :)

---

### Post by essjay612 on 2006-06-16
[QUOTE=yager]Read in to the responses.  There are several individuals who add to the discussion about half way in to address the use of a boot floppy and a CD method for booting with GRUB to the USB device.  It gets a little long in some places with all the Q&A but it is in there.  Zerlinna provided a link at this location.
[http://www.ubuntuforums.org/showpost.php?p=865194&postcount=334](http://www.ubuntuforums.org/showpost.php?p=865194&postcount=334)

This is the 334th message in the thread.[/QUOTE]

Here's a question, though.  From what I can tell, those instructions take an image of the boot folder and place them on a CD.  Isn't this, in essence, the same thing I did when I installed Ubuntu to a secondary IDE drive (hdb)?

Here's what I'm thinking:  

1. Install Ubuntu to sda2 (has to be partition 2...can't get around it).  
2. Install GRUB to sda2 along with the rest of Ubuntu.  
3. Run bootpart on the newly created Ubuntu install (sda2).  What bootpart does is copies an image of the boot folder and creates the file "bootsect.lnx", which is placed on my primary IDE drive (hda) at c:\bootsect.lnx.
4. Update c:\boot.ini in Windows so that I get a choice when I turn the computer on.  
5. When I select Linux at boot, NTLDR references bootsect.lnx (the copy of my boot folder) and then passes control to GRUB on my sda2 drive.

Isn't that the same thing as making a boot CD?  I'm no expert, but from what I'm reading, that's what she's suggesting.  Making an image of the /boot folder and burning it to a disk.  I can't try any of this yet because I'm out of town (going home tomorrow, Saturday), but when I get home I will definitely try this.  

So all you Ubuntu/Linux experts out there...wouldn't the above steps work, in theory, the same way that a boot cd does?  And if it does, should I post a "howto" somewhere?  

Thanks, all.  :))

---

### Post by yager on 2006-06-16
Your idea may work.  I remember someone offering the boot.ini idea as an option and that it worked for them.

A simpler approach might be to just put GRUB on your primary drive.  Then you can set up GRUB to boot either Windows or Ubuntu on the external drive.  If this does not work, you can wipe GRUB with fdisk /MBR from Windows.  You may want to have a bootable floppy or CD handy so you can issue this command if anything goes bad.

---

### Post by essjay612 on 2006-06-17
[QUOTE=yager]Your idea may work.  I remember someone offering the boot.ini idea as an option and that it worked for them.

A simpler approach might be to just put GRUB on your primary drive.  Then you can set up GRUB to boot either Windows or Ubuntu on the external drive.  If this does not work, you can wipe GRUB with fdisk /MBR from Windows.  You may want to have a bootable floppy or CD handy so you can issue this command if anything goes bad.[/QUOTE]

Actually, I ended up selling my External drive to a friend for $75 and using that to buy a new 80Gb internal drive, so my problem is solved.  I think, though, that my friend is going to try it when he picks up the External...so I'll let everyone know how it went.  

Thanks again for the replies.  They're appreciated.  :))

---

