---
title: "Problem Installing.."
date: 2009-11-25
forum: General Help
---

### Post by kevinwmiller on 2009-11-25
I'm trying to install Ubuntu 9.10 on my laptop, and when I get to "partitioning" section, it unfortunately isnt the same partition manager that you see on all the graphical tutorials.  
 
On most of the tutorials, its just a "Check if you want to use all the hard disk" option and go forward.  I dont even have that option, it wants me to do it all manually and I'm somewhat clueless as to how to do that.

Any clues?

---

### Post by audiomick on 2009-11-25
Hi Kevin,
Read this
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
should explain it. And don't panic, it is not as hard as it looks.

Have you perhaps got the "Alternate CD ", and not the live CD? That would explain why it is different.

---

### Post by mkvnmtr on 2009-11-25
On my install of 9.10 I seem to remember having the chance to click on use the whole disk. Did not use it I always use the manual option. Maybe you should click the back button and see if you missed something. I have  done that plenty of times.

---

### Post by kevinwmiller on 2009-11-25
I think I have the partition right.

I have a 320GB HD,

/dev/sda1 ext3 /home  308 GB
/dev/sda2 ext3 /          10   GB
/dev/sda3 swap             2   GB

Is this right?  Or look right?  Also, I used the first two, sda 1 & 2 marked "Primary" and the 3rd as logical.  Is this correct?

I'm not sure as to the difference between primary and logical. lol.

Trying not to panic, I just really like linux, but dont want to break anything.

---

### Post by emachnic on 2009-11-25
It's usually easier to do

/dev/sda1 ext4 /
/dev/sda2 swap

---

### Post by kevinwmiller on 2009-11-25
Ok, so now I tried what I showed you, and it says it failed.  

The ext4 file system creation in partition #1 of SCSI1 (0,0,0) (sda) failed.

Oh, and all of a sudden, after it fails, the fancy graphical interface has poped up.  So I chose "Erase the disk" and it gave me the above ex4 file system error.  now im trying to install them side by side, to see if that will work.

---

### Post by kevinwmiller on 2009-11-25
I think the problem is that I'm use UNetbootin, and am booting from the harddisk, and not a USB or disk.  My next task, if this fails, is to try to do all of this from a USB, as I have no disks. 

What do you think?

I agree with you emachine, but now its doing this graphical interface thingy, so its doing it all by itself...and failing. lol

---

### Post by emachnic on 2009-11-25
If you boot from hard disk, you can't install on said hard disk. Have to boot via USB or LiveCD

---

