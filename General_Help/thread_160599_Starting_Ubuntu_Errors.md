---
title: "Starting Ubuntu Errors"
date: 2006-04-15
forum: General Help
---

### Post by cached on 2006-04-15
I recently had my cat walk on my keyboard and after I pulled him off I realized that the menu in the top left corner was gone.  I didn't think much of it, so I restarted the computer in order to fix the problem.  While Ubuntu was booting up, however, it gave me an error like this:

> Mounting /dev/hda1 onto /root. Invalid Operation

and then a few more errors. When I run knoppix I can see all the files on this hard drive, but when I run windows (its a dual-boot system using 2 different hard drives) using something that allows me to read/write to *nix hard disks, it claims that this hard drive is about 8 megabytes (while its really 147 GB) and that the only thing in this drive is an item called Recycled.

What should I do? ](*,)

---

### Post by jamardi on 2006-04-15
Hi cached. 
I supose you where talking about the [Window$' ext2/ext3 driver]("http://www.fs-driver.org/"), in that case my advice is to be carefull with that: >  The current version of the Ext2 file system driver does not maintain access rights (this means that Window$ will create a copy of the lovely Thumbs.db on each directory you browse for example.).
However, i'd try to boot from a livecd, p.e. Knoppix, make chroot /dev/hda1 (where /dev/hda1 is your root partition) and take a look at /etc/fstab or execute fsck to check if the filesystem is alright...
Hope it helps...

---

### Post by cached on 2006-04-15
I just realized I was incorrect: I CANT access any file on the hard drive.  The error I get while trying to access it from Knoppix is: 

Could not mount device.
The reported error was:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

---

### Post by bscbrit on 2006-04-15
The first thing to do is not to use any Windows software to try to fix your drives.  Neither system is particularly good at reading the other, at least not to the level for fixing things.  There are numerous stories of partition managers in one failing to comply with the needs of the other.  Stick with Knoppix or something similar.  If K can still see all of your partitions and data then everything would appear to be recoverable.  The second thing is to shoot the cat, or at least stop it from walking on your keyboard!

Can you boot your computer in recovery mode?


EDIT - I obviously didn't type fast enough....

---

### Post by bscbrit on 2006-04-15
I am, however, curious as to what combination of keys the cat pressed that caused such a problem - surely it didn't accidentally type your password in response to 'sudo' and I cannot imagine how it could have done something quite so severe from the keyboard.  Just hope that it wasn't static from the cat zapping your computer - that might be a completely different story.

---

### Post by bscbrit on 2006-04-15
If you can't mount it - you can't fix it.  Try running fsck from Knoppix to see if it can recover the partition.  If not, get out the original Ubuntu disks and make yourself a pot of coffee....:D  Oh, and get your backups from your archive.  Hello, hello - you have got backups haven't you?  (I've taken this as a reminder to make sure that my OWN backups are up to date)

---

### Post by cached on 2006-04-15
[QUOTE=bscbrit]Try running fsck from Knoppix to see if it can recover the partition.  [/QUOTE]

Thanks! It worked after about 2500 questions (I had to hold down enter for a LONG Time ;))

You're right, I should backup stuff.  Thanks for that reminder as well.

---

