---
title: "Moving /Home to another drive - help"
date: 2009-11-15
forum: General Help
---

### Post by scotc on 2009-11-15
Dear Ubuntu lads and lasses,
I am trying to move my home folder to another logical drive and I have tried all the "how to"s over the last three days, including Psychocats.

My situation is a little different to those documented and in trying to interpret and adjust I am apparently making mistakes.

I have one physical drive, SDA.  Partitioned logically.

Sda1 = windows partition   [ Dual boot, not relevant for this]
sda2 = Gutsy file system, including /home
sda3 = shared drive of data (docs, photos etc) - called "E-drive"
sda4 = swap

I want to MOVE the /home dir to the shared "E-drive", sda2, alongside the existing data so that if I need to clean install linux on the other drive, I won't loose /home.

I have a few gig of empty space on all three logical drives.

I was NOT planning to partition a new drive or resize, hence my differing from the instructions out there.

I just want to MOVE home and have linux find it on boot on sda3 (E-Drive).

I won't detail all the methods tried, but if someone could give me a step by step account of how to move, mount and edit the fstab, I would appreciate.

This is the fstab.
-------
# /etc/fstab: static file system information.
#
# <file system> 				<mount point>   <type>  <options>       <dump>  <pass>
proc            				/proc           proc    defaults        0       0

# /dev/sda2 Linux system
UUID=fce0dcf6-0a6c-4243-86a1-b4a49c8726e1	/               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1 Windows system
UUID=460C7F970C7F80AB 				/media/sda1     ntfs    defaults,umask=007,gid=46 0       1

# /dev/sda3 E-Drive
 UUID=21ba8398-cca2-4bc9-a327-fcb447bb4c1f	/media/sda3     ext3    defaults        0       2

# /dev/sda4	
UUID=435ca6ea-643e-4057-8112-6c7e43f08a37 	none            swap    sw              0       0

/dev/scd0      					/media/cdrom0   udf,iso9660 user,noauto,exec 0       0
---------
Many thanks, Ubuntu users.

---

### Post by Dakra on 2009-11-15
In the fstab file, edit /dev/sda3:
```
# /dev/sda3 E-Drive
 UUID=21ba8398-cca2-4bc9-a327-fcb447bb4c1f /home     ext3    defaults        0       2

```And it should be enough. By default your current configuration and settings are in your current /home so the fstab edition will reset your desktop to its original state. But if you copy those files (hidden files > CTRL+H in nautilus) in your new /home, it should be ok.

Here is my source:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)


And if you have no data on your Windows partition, I think you should remove it from the fstab. No need to mount that partition automatically if you don't use it in Ubuntu, I think it increases the risk to do a bad move in it.

---

### Post by tom4everitt on 2009-11-15
I agree. 

But start with copying your home folder to sda3. That is, if your user is scotc, you should have a folder named scotc on sda3. Do this by dragging the scotc folder in your /home directory to /media/sda3 so all the hidden files comes along. (Or use cp -r /home/scotc /media/sda3/).

Then do the above change to fstab, and restart your system.

---

### Post by louieb on 2009-11-15
Just seems strange that your calling that partition the E-drive. Makes it sound like It uses some MS file-system format.(NTFS)?  What is its file-system format?(NTFS,ext3,..)

---

### Post by scotc on 2009-11-15
Thanks to Tom and Dakra for help.
It didn't go so well.
Ubuntu is not booting now  (I am posting via winxp dualboot)

I copied the old /home folder to the new location using rsync, as I believe it gets all hidden files most reliably.  
The copy command was "sudo rsync -axS --exclude='/*/.gvfs' /home/scot/. /media/sda3/."
That being I think the location syntax that you suggested before, Tom.

Only thing was that the "sda3 E-drive" already had a folder with my user name on it.
That is to say "scot".  It sits beside my wife's folder "sam" so as to hold our respective files.


Rsync dumped all the copied files in "scot" beside my existing docs, folders, pictures etc.

The directory does not refer to "home" at all.
Is that why the OS can't find what it needs to boot?

Next. Using the live CD to boot, I can see on the sda2 linux filesystem drive that /home still exists, even though at one point I renamed it "old_home".

I can't alter anything on either drive, like fstab file, because I have no permissions on these drives via the live CD.  Is there a way to alter that?

I think that my current fstab does not refer to "/home" but only to mounting the "sda3 E-drive" as /media/sda3.

From XP I can't get to the fstab file as XP can't see that drive because it's ext3.

How do I recover the ubuntu filesystem's ability to boot, with sudo permissions so that I can restore the previous incarnation and start again?

---

### Post by scotc on 2009-11-15
Thanks to Tom and Dakra for help.
It didn't go so well.
Ubuntu is not booting now  (I am posting via winxp dualboot)

I copied the old /home folder to the new location using rsync, as I believe it gets all hidden files most reliably.  
The copy command was "sudo rsync -axS --exclude='/*/.gvfs' /home/scot/. /media/sda3/."
That being I think the location syntax that you suggested before, Tom.

Only thing was that the "sda3 E-drive" already had a folder with my user name on it.
That is to say "scot".  It sits beside my wife's folder "sam" so as to hold our respective files.


Rsync dumped all the copied files in "scot" beside my existing docs, folders, pictures etc.

The directory does not refer to "home" at all.
Is that why the OS can't find what it needs to boot?

Next. Using the live CD to boot, I can see on the sda2 linux filesystem drive that /home still exists, even though at one point I renamed it "old_home".

I can't alter anything on either drive, like fstab file, because I have no permissions on these drives via the live CD.  Is there a way to alter that?

I think that my current fstab does not refer to "/home" but only to mounting the "sda3 E-drive" as /media/sda3.

From XP I can't get to the fstab file as XP can't see that drive because it's ext3.

How do I recover the ubuntu filesystem's ability to boot, with sudo permissions so that I can restore the previous incarnation and start again?

---

### Post by dcstar on 2009-11-15
> **scotc said:**
> Dear Ubuntu lads and lasses,
I am trying to move my home folder to another logical drive and I have tried all the "how to"s over the last three days, including Psychocats.

My situation is a little different to those documented and in trying to interpret and adjust I am apparently making mistakes.
...........
I want to MOVE the /home dir to the shared "E-drive", sda2, alongside the existing data so that if I need to clean install linux on the other drive, I won't loose /home.
..........
Many thanks, Ubuntu users.

You just cannot "move" /home to existing partitions using methods that mount the partition - /home is a Linux system folder that has specific security requirements and trying to mix it with an existing filesystem will be fraught with problems.

If you do not want to create a fresh /home partition (which is ONLY used for /home) then your best bet would be to create a folder on the EXT3 drive with the available space, then copy all of the /home contents to it (using a Live CD) and then make a soft link to it to replace the original /home folder.

---

### Post by scotc on 2009-11-15
> **dcstar said:**
> You just cannot "move" /home to existing partitions using methods that mount the partition - /home is a Linux system folder that has specific security requirements and trying to mix it with an existing filesystem will be fraught with problems.

Thanks David for the above.  I wish I'd known that before I did it.

I don't fully understand your answer (newbie).  I couldn't copy / write to my sda3 ext drive with a live CD because I don't have permission when in live CD.

I don't know what or how a "soft link" is created.

More urgently, I don't know how to recover / get my system to boot at the moment.
It loads grub, gives me the menu.list.  I pick ubuntu, the screen goes blank, the HD twitters for a moment or two then the system just sits there.  Hard shutdown required.

I tried booting into recovery mode to restore my fstab, but I didn't get too far because permissions not given and I don't know the commands too well.

---

### Post by scotc on 2009-11-15
I'm going to move this discussion to a new thread because I now need help to recover the system

---

### Post by scotc on 2009-11-16
Dear all, I recovered the system so here it is for those who follow in my footsteps into the wilderness.

The Fstab was hosed, probably by removing the windows Sda1 drive, which according to Gparted is flagged as "boot".  I suspect that removing it meant that linux on sda2 could not boot because some part of grub /mbr was on the windows drive.

Trying to edit the fstab was a waste of time because Recovery Mode and Live CD found the drive to be read only.

I realised that I did have a way to read the drive - from windows via ext2fs programme, which for those that don't know is a wee prog that allows Windows to read and write to an ext2 drive i.e. a linux file system.  I use ext2fs to read the 3rd partition (shared) where all the docs created in windows and linux reside.

I knew it would override any permissions.

By my own default, windows would not mount the linux drive, so as usual I hadn't seen it when scrabbling around in windows trying to problem solve.

I simply gave the linux os drive a letter (z:) via the wee programme, then I could enter it and tweak the fstab with Textpad.

Sorted.

---

