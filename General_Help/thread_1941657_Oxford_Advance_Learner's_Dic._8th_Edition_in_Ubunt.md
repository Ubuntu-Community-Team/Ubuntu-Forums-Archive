---
title: "Oxford Advance Learner's Dic. 8th Edition in Ubuntu"
date: 2012-03-16
forum: General Help
---

### Post by tanvsb on 2012-03-16
I'm usuing Ubuntu 10.10. Few days before I brought an Oxford Advance Learner's Dictionary 8th edition. I got a CD along with the book. Both in the book and the CD  Ubuntu is imentioned in the system requirement for installation. I think that means it could be installed in Ubuntu. But when I enter the CD using my ubuntu, it doesnt show the drive or mounts. Therefore, I am not able to install it in ubuntu. can anyone help me out how to install it in ubuntu or inform me either is it actually possible to install it there?

---

### Post by raja.genupula on 2012-03-16
are you sure with you DVD Writer/Reader and CD status , i mean are they good ?

---

### Post by tanvsb on 2012-03-16
> **raja.genupula said:**
> are you sure with you DVD Writer/Reader and CD status , i mean are they good ?

Yes, I've checked... my DVD writer/reader is good;  It's working well.

---

### Post by raja.genupula on 2012-03-16
check the CD also , i mention there already . put it on other systems and check the CD i mean is it working or not .

---

### Post by wyliecoyoteuk on 2012-03-16
Look at this thread

[http://ubuntuforums.org/showthread.php?t=1211149](http://ubuntuforums.org/showthread.php?t=1211149)

---

### Post by tanvsb on 2012-03-16
> **raja.genupula said:**
> check the CD also , i mention there already . put it on other systems and check the CD i mean is it working or not .

There is no CD rom in my computer and I checked it works in windows without any problem.

---

### Post by tanvsb on 2012-03-16
> **wyliecoyoteuk said:**
> Look at this thread

[http://ubuntuforums.org/showthread.php?t=1211149](http://ubuntuforums.org/showthread.php?t=1211149)

I checked that before. That is a very old thread and now doesnt work actually....

---

### Post by tanvsb on 2012-03-17
Well, I was able to install the OALD 8th Ed. in my Ubuntu 10.10. I mailed to the help dest of OALD authority and they mailed the following process which I followed and able to install it in my system. For everybody I'm going to share it...

 [B]Step 1: 
    
  [/B]Ubuntu probably won't mount the CD when it is loaded because it is  mixed mode and auto-mounting fails. To install, insert the CD and open a  terminal. Find out what your CD is called ... $> sudo lshw -C disk
 . . .
 *-cdrom
      description: DVD-RAM writer
      product: DVD RW AD-7201S
      vendor: Optiarc
      physical id: 1
      bus info: scsi@3:0.0.0
      logical name: /dev/cdrom
      logical name: /dev/cdrw
      logical name: /dev/dvd
      logical name: /dev/dvdrw
      logical name: /dev/scd0
      logical name: /dev/sr0
      version: 1.09
      capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
      configuration: ansiversion=5 status=ready
 [this output will (of course) vary from PC to PC - it’s the ‘logical name’ for the CD that you will be looking for]
 
 **Step 2:** 
  
You'll  need a mount point to 'borrow', so open Nautilus (the file manager) and  go to file system, media (/media). There should a spare mount point you  can 'borrow' – most PCs have 'floppy0' that isn't used by the system.
 

 [If  you don't have a spare one, have a look at this page [[1] ] and create  your own. If you do, just use that instead of /media/floppy0 in the  example below] 

***** *In may not get the folder floopy0 in /media. You have to create that folder there with root privilege.***

[B]
Step 3:
    
  [/B]Back to the terminal ... you need to use:
  

 $> sudo mount -t iso9660 /dev/cdrom /media/floppy0
  

 to specifically indicate the file system
 An icon should appear on the desktop. Careful though: right click – 'open with autorun prompt' (seems sensible!) bombs!
  

 [B]Step 4:
  [/B]

 So  open the mounted volume in Nautilus (or any file manager), go to the  'linux' directory and find 'setup.sh'. Double click and choose 'Run in  Terminal' – if you choose 'Run' it won't install as it expects you to  scroll through the user agreement first – which you can only do in a  terminal.
  

 [B]Step 5:
  [/B]

 This installs a desktop icon.  Double clicking just gives a warning message and it fails to run. Right  click the shortcut and check the 'Allow executing ... ' on the  Permissions tab.
 thumb|Description
 OALD8 should now run.
 The mounted drive (no longer needed) will clear on a re-boot or you can run:
 $> sudo umount /media/floppy0
 to close it
 
Thanks to all....

---

