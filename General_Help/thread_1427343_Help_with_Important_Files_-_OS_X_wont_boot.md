---
title: "Help with Important Files - OS X wont boot"
date: 2010-03-11
forum: General Help
---

### Post by iVerdugo on 2010-03-11
Starting from the beggining, i was working in this Macbook (its my mothers i do not use apple very much), just looking at youtube and normal stuff. no installations or anything, only used my external harddrive.
Next time i turned on my computer, this weird gray screen showed up with something written like "kernel mismatch from your hardware" or something like this, i panicked and didnt know what to do so i restarted like the message in multiple languages said so. Nothing happened.

I tried to boot from CD (press C key) and it worked so i went on disk utility and looked for errors but all says fine. I tried making a copy of the Macintosh HD to my external hard drive so that i could re install mac but after a while copying it stops and gives me an error saying "operation not supported".

I asked a professional and he suggested using a live cd of Linux (ubuntu 9. ) to try and retrieve my files from there. I did this and the live cd worked and i could see into all my folders but when i went to /Users/myuser/ none of those folders would let me copy, open and see the files. Desktop is where the important data is. It gave an error file permissions. I cant compress, open, see the files nor copy them.

This is very annoying as the files are extremely important and i cannot do anything to delete them.

My avaliable resources:

500gb external hard drive
Macbook Pro
Linux Ubuntu
Apple Original Install DVD (Snow Leopard)
Please help me find a way to retrieve these files and copy them onto something. I really need this with urgency. Thanks to everyone who takes a minute to read this.

---

### Post by flippo on 2010-03-11
Boot the live cd, get to the desktop environment:

Open a terminal (Applications -> Accessories -> Terminal)

Is your Mac partition mounted?
If you dont know, type "df -h" into the terminal, look for an entry with HFS+ as its filesystem

If it is mounted:
Look at the output of "df -h" That will tell you where your mac partition and external hard drive are mounted under the "mount point" part (most likely something like /media/mac or /media/disk).  Once you figure out where they are mounted type this into the terminal:```
gksudo nautilus <macpartitionmountlocation>
gksudo nautilus <externalHDmountlocation>
```

This should allow you to move your data from one partition to the other.  If your external is mounted with HFS+ then you may only be able to mount it read-only, in which case this wont be of much help to you.  If just your mac partition is HFS+ then your fine, as you only need to read from it.

If it is not mounted:
To mount a device:
```
sudo mkdir /media/<mountpoint>
``` you may make mount point whatever you wish.  Now find out what the device's /dev listing is:```
sudo blkid
```Then mount the device```
sudo mount /dev/<devlisting> /media/<mountpoint>
```Now refer to the If mounted portion.

If you need further assistance please post.

---

### Post by coffeecat on 2010-03-11
Two suggestions:

Try booting up your Mac again and when you get to the grey screen and the "kernel mismatch" error message, copy it down exactly as it appears. No spelling errors. No "or something". Then google the error message. Someone, somewhere will have had the same error as you, posted on a Mac support forum and got an answer and, hopefully, a fix.

Suggestion 2:

The reason you got a file permission error when you tried to access your Mac home folder is down to Unix permissions. Both MacOS and Linux use the same system of permissions which define a UID (user identity) number. Your Mac UID is probably 99. The temporary user (account name = "ubuntu") in a live CD session must have had a different UID. That is why you get the access denied.

Therefore, boot up with the Ubuntu live CD and plug your external drive in so that it is mounted and a Nautilus (file browser) window opens. Now go to Places and click on your Mac partition so that it is mounted, but close the Nautilus window that opens showing your Mac filesystem (if it opens). Now open a terminal and do:

```
gksudo nautilus
```That will open a nautilus window with elevated administrator privileges. When it opens it will open the /root folder of the live filesystem. Click the up button to go to the parent folder (which is the root of the live filesystem) and then double-click on /media. You should find a folder in /media in which the Mac partition has been mounted. Double-click on that and you'll be in the root of the Mac filesystem. You can't do any damage because Ubuntu can only read (not write to) the journalled hfs+ filesystem of your Mac. But you do have root privileges and should be able to copy anything. Navigate to /Users/myuser and copy anything you want to your external drive with drag and drop.

I'm assuming here that the external drive is formatted with NTFS or FAT32, otherwise please post back with details. And don't forget that FAT32 has a maximum file size of 4GB, so if that's FAT32 and you have big video files you may have problems.

---

### Post by iVerdugo on 2010-03-11
About the Kernel error, it is a very huge error, the whole page screen more or less. Also, how do i copy this? Hand written?

My harddrive has been converted to NFTS and i will try to change the UID.

Thank you both for your quick replies and i will do what you guys suggested and report my results

---

### Post by coffeecat on 2010-03-11
> **iVerdugo said:**
> About the Kernel error, it is a very huge error, the whole page screen more or less. Also, how do i copy this? Hand written?

Find a distinctive phrase and google that. Error codes - if any - are useful.

> **iVerdugo said:**
>  My harddrive has been converted to NFTS and i will try to change the UID.

You can't change the UID - not on the Mac hfs+ filesystem. You can't write it. Also, UIDs are irrelevant when you're dealing with NTFS - being a Microsoft filesystem it doesn't support Unix permissions. Which, in this situation, is to your advantage. Just to be clear. Use a root nautilus to copy from the Mac partition so that you can get into your personal folders, and copy into an ordinary nautilus window showing your NTFS external drive. Once the files are copied onto the NTFS filesystem, you've 'lost' the Unix permissions. Until such time as you copy them back onto a Linux or Mac filesystem, that is.

Good luck.

---

