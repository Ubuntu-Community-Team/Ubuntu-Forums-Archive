---
title: "&quot;Kill Me&quot; Error when installing??"
date: 2006-04-07
forum: General Help
---

### Post by Simimi on 2006-04-07
I recently got ahold of a 500 mhz windows 98 SE box, which is a huge upgrade from my 233 Mhz Ubuntu Box. I'm new to Linux and love learning all the new things i get to everyday, but this... this is insane...

After trying to install Ubuntu from the disk right from the website via Ship-it, on this particular box, 11 times... I get the same message, which I have never seen before...and I have put Ubuntu on almost 20 computers methinks...

When the install gets to the disk partitioner "Now Loading Disk Partitioner..."
the screen goes to an all black-terminal style screen, and it spams the phrase "kill me" like so..

kill me
kill me
kill me
kill me
kill me
kill me
kill me

Anyone ever seen this before? Know how i can fix it and get Ubuntu on this box?

I thought about formatting the HDD but I..do not know how inside of windows and nothing I found online was very helpful...

 Love,
   Mimi

---

### Post by dcstar on 2006-04-07
[QUOTE=Simimi]
.....
I thought about formatting the HDD but I..do not know how inside of windows and nothing I found online was very helpful...
[/QUOTE]
Go here and download (and burn) this handy tool, it should allow you to boot up off it and manually format/partition your disk:

[http://www.sysresccd.org/Index.en.php](http://www.sysresccd.org/Index.en.php)

---

### Post by Simimi on 2006-04-07
Hmm I do not have a cd burner, or access to one... all I know is It (the computer) will not let me install Ubuntu...and I do not want to use Windows!
Any other ideas friends?

EDIT: Also a note, I COULD install FreeBSD from a version 5.0 disk a friend gave me, but it has no GUI when I install it (and apparently to me, does not use the Bash-shell...) but I can not install Ubuntu, which is what I learned Linux on, and love.

Love-mimi

---

### Post by truNWA on 2006-04-07
Thats a very disturbing message....... The only think i would suggest is get another disk from ship.it

---

### Post by elamericano on 2006-04-07
If you have a floppy, you could make a bootable floppy from Win98, boot from that, and format your harddrive FAT32. If that doesn't allow you to reformat to Ext2 or 3 during Ubuntu install, I think you could use it as FAT32 if you had to.

It would be better if you had a live CD, but in the meantime, you might find another solution by experimenting. Let us know how it goes.

---

### Post by elamericano on 2006-04-07
Great bug, by the way. I've never seen a computer that wanted to end it all :D

---

### Post by Simimi on 2006-04-07
I have several live cds, how would those help me?
Yes this is very interesting, never seen this before, but it just will not let me run the partitioner...and I have tried using non-official cds (cds of ubuntu not from ship-it) and this happened prior to my ordering my ship-it cds.

I'm running out of ideas here, and using windows scares me...I miss linux... :'(

Love-mimi

EDIT: The drive is already FAT32...if that helps?

---

### Post by zapcojake on 2006-04-08
There used to be a boot floppy at Icewalkers.com called Nuke or hardrive nuke or something like that.  I have an old computer that was a Rent-a-center model and it wouldn't let me install Ubuntu on it either.  I used an ipcop cd to wipe the drive and then installed ubuntu.

---

### Post by elamericano on 2006-04-08
I was thinking of fixing a drive error that may be affecting your partitioning. If you have a live linux cd you should be able to boot one of those and format the hard drive to Ext3.

To create a new partition on /dev/hda (I'm assuming your drive is hda):
fdisk /dev/hda
p (to list existing partitions)
d (to delete each partition)
n (to create a new partition)
p (of type primary)
1 (partition # 1)
Enter (default start cylinder)
Enter (default end cylinder)
w (to write new partition table - nothing is written until here, then everything is erased.)

The command to format is:
mke2fs -j /dev/hda1

After this you may be able to install ubuntu by skipping disk partitioning and formating ("use existing file system" option)

---

### Post by Simimi on 2006-04-08
Well the Ubuntu live CD will not Boot either for some odd reason... it will only go up to "creating user account" then it freezes at 56%

Also, what if I plug in my old hard drive that had Ubuntu on it before? LEt me try that, it might work... thanks for everything! 
 Love-mimi

---

