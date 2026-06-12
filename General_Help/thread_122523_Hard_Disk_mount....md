---
title: "Hard Disk mount..."
date: 2006-01-27
forum: General Help
---

### Post by Downtown on 2006-01-27
Let me explain...

While trying to resize a secondary NTFS drive so that I have more space to save files on Ubuntu (which is on a seperate drive than the one in question), I got some major error that corrupted my filesystem.  So I said, what the hell, all that data's lost already, might as well format it for use on Linux.  So I reboot and run a Gparted live disc on startup.  I use that to format the drive and make it ext3.  Then I reboot and start up Ubuntu.

I go to System>Administration>Disks and set the drive Access Path to /bigdrive.  I then go to /bigdrive and there is a file in there called Lost+Found which I cannot touch, and the whole drive is write-protected.

I want to know how I can enable acess to the drive and make it read/writeable.

---

### Post by earobinson on 2006-01-27
post your /etc/fstab

also do an ls -la on the dir that has bigdir in it make sure that all users can read and write to it

---

### Post by Downtown on 2006-01-27
fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1       /bigdrive        ext3   umask=0000       0       0

---

### Post by earobinson on 2006-01-27
and the ls?

---

### Post by Downtown on 2006-01-27
ls -la...

total 24
drwxr-xr-x   3 root root  4096 2006-01-27 18:02 .
drwxr-xr-x  23 root root  4096 2006-01-27 19:01 ..
drwx------   2 root root 16384 2006-01-27 18:02 lost+found

---

### Post by Downtown on 2006-01-27
no help?...

---

### Post by Downtown on 2006-01-27
bump...

---

### Post by Downtown on 2006-01-27
I think my problem is with fstab.  My Ubuntu primary drive is hdb, and the secondary drive that I want to put my files on is hda1.  fstab is currently...

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hdb1 / ext3 defaults,errors=remount-ro 0 1
/dev/hdb5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hda1 /bigdrive ext3 defaults,errors=remount-ro  0 0

Does anybody know what it should be for my situation?

---

### Post by Downtown on 2006-01-28
Okay.  Rephrase of my question.  What should fstab be if I want two hard drives mounted, the main setup on hda1, and both of them read/writeable by Ubuntu.  Is there any special setup I need to do?

---

### Post by Xcopy on 2006-02-01
Ok, if you want to read/write the new mount try this:

first mount /dev/hda1 in /bigdrive.

second, open a terminal an write this:
sudo chown -R user:user /bigdrive

where user is your main user (not root).

and in your fstab try this

dev/hda1 /bigdrive ext3 defaults,errors=remount-ro 0 1

with this you can write the new mounts.

Enjoy :-D

---

### Post by Downtown on 2006-02-01
Actually, thanks for not replying sooner.  I figured it out by fiddling with stuff cuz I needed to have it done, and I'm kinda impatient.  I forget now how I did it, but long story short, I'm back on Windows.  Don't worry, I'm not selling out, I didn't pay them a dime.

---

