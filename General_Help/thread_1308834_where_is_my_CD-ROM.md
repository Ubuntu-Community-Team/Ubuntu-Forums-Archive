---
title: "where is my CD-ROM?"
date: 2009-10-31
forum: General Help
---

### Post by dribuu on 2009-10-31
hi,:D

I couldn't mount my CD-ROM,

there's no /dev/cdrom or /dev/hdc,

when I use "sudo mount /dev/cdrom /media/cdrom",it said "/dev/cdrom does not exist"

also I set CD-ROM boot in bios help nothing.

My ubuntu need a completely reinstall, I bought a new hard disk, but there is a problem with CD-ROM.

I need your help, give me some suggestions, thanks!

---

### Post by undecim on 2009-10-31
your cd drive should be /dev/sr0. Any /dev/cdrom, /dev/dvd, etc are just symlinks to /dev/sr0

---

### Post by undecim on 2009-10-31
Also, if you want to use the cdrom symlink, look for something like /dev/cdrom0

---

### Post by sickly on 2009-10-31
This might help you
 
[http://fixunix.com/help/542793-mount-cant-find-media-cdrom-etc-fstab-etc-mtab.html](http://fixunix.com/help/542793-mount-cant-find-media-cdrom-etc-fstab-etc-mtab.html)

---

### Post by 3rdalbum on 2009-10-31
It might be /dev/scd0

---

### Post by dribuu on 2009-10-31
> **undecim said:**
> your cd drive should be /dev/sr0. Any /dev/cdrom, /dev/dvd, etc are just symlinks to /dev/sr0

thanks for replying so quickly.

I ls my dir found:
**************************
ubu@ubu-laptop:/dev$ ls s*
sda  sda1  sda2  sda5  sequencer  sequencer2  sg0  snapshot  sndstat  stderr  stdin  stdout

shm:
pulse-shm-2635008962  pulse-shm-332300129

snd:
controlC0  pcmC0D0c  pcmC0D0p  seq  timer
***************************

Is sg0 the CD-ROM? when I "sudo mount /dev/sg0 /media/cdrom
"
it says "mount: /dev/sg0 not a block device
"

any suggestions

---

### Post by sickly on 2009-11-01
did you go to 
 
places>computer
 
and see if its already mounted?

---

### Post by dribuu on 2009-11-01
> **sickly said:**
> This might help you
 
[http://fixunix.com/help/542793-mount-cant-find-media-cdrom-etc-fstab-etc-mtab.html](http://fixunix.com/help/542793-mount-cant-find-media-cdrom-etc-fstab-etc-mtab.html)

I tried these:

mkdir /media
mkdir /media/cdrom
mount /dev/cdrom /media/cdrom


I get the same message, no device

---

### Post by cascade9 on 2009-11-01
> **dribuu said:**
> also I set CD-ROM boot in bios help nothing.

My ubuntu need a completely reinstall, I bought a new hard disk, but there is a problem with CD-ROM.

Is the BIOS seeing the CD rom? If its not, your never going to see it in Ubuntu. 

Since you bought a new HDD, I'll take a guess. Is it an IDE HDD and CD rom? Are they on the same IDE channel?  If the CD Rom and the new HDD are both set to master, or both set to slave, then you wont see one of them.

---

### Post by efflandt on 2009-11-01
Do you get anything for: **ls -l /dev/*cd***

efflandt@efflandt-laptop:~$ **ls -l /dev/*cd***
lrwxrwxrwx 1 root root  3 2009-10-31 18:52 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root  3 2009-10-31 18:52 /dev/cdrw -> sr0
lrwxrwxrwx 1 root root  3 2009-10-31 13:52 /dev/scd0 -> sr0

/dev/pktcdvd:
total 0
crw-rw---- 1 root root 10, 61 2009-10-31 13:52 control

(note the symlinks to sr0, pktcdvd is DVD writer, same actual device)

efflandt@efflandt-laptop:~$ **ls -l /dev/sr0**
brw-rw----+ 1 root cdrom 11, 0 2009-10-31 13:52 /dev/sr0

Of course you need to prefix mount commands with "sudo " to run mount as super user.

---

