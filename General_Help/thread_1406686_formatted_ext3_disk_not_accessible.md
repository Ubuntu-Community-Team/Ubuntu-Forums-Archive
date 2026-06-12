---
title: "formatted ext3 disk not accessible"
date: 2010-02-14
forum: General Help
---

### Post by RonaldVR on 2010-02-14
I run Ubuntu from the DVD to format an external USB disk drive as ext3.

All seems to go well, but I cannot access the disk. 

Create folder and create file are grayed out and copying files to the disk gives a security error.

My hard disk recorder that supports ext2/ext3 disks doesn't recognize the disk as an ext3 and my Windows PC's with EXT2IFS installed do see the disk but say it isn't formatted.

I tried this with ext2 as well: same results throughout.

What am I doing wrong?

thanks for assistance.

---

### Post by Morbius1 on 2010-02-14
You've got two different problems it seems.
> but I cannot access the disk. Because the external USB device is automaounted with owner = root.

You will need to either change ownership to you, for example:

**sudo chown -R ronald /media/whatever**

Or leave the owner as root and change permissions to allow anyone to read and write to the device, for example:

[B]sudo chmod -R 0777 /media/whatever
[/B]> My hard disk recorder that supports ext2/ext3 disks doesn't recognize the disk as an ext3 and my Windows PC's with EXT2IFS installed do see the disk but say it isn't formatted.I'm not sure what to make of that. Sorry

---

### Post by RonaldVR on 2010-02-14
> 
Or leave the owner as root and change permissions to allow anyone to read and write to the device, for example:

[B]sudo chmod -R 0777 /media/whatever
[/B]

thanks, this works, but it doesn't seem to make sense: I formatted the drive as root and tried to write to it as root, so why do I have to set permissions to allow myself to write? Never mind, so far so good.

---

### Post by RonaldVR on 2010-02-14
> **RonaldVR said:**
> I run Ubuntu from the DVD to format an external USB disk drive as ext2.

My Windows PC's with EXT2IFS installed do see the disk but say it isn't formatted.



It seems the graphical Ubuntu formatter defaults to an inode size of 256 whereas EXT2IFS can only handle 128 bytes. I am now trying to format using the command line utility mke2fs with the option -I 128.

---

### Post by RonaldVR on 2010-02-14
> **RonaldVR said:**
> It seems the graphical Ubuntu formatter defaults to an inode size of 256 whereas EXT2IFS can only handle 128 bytes. I am now trying to format using the command line utility mke2fs with the option -I 128.

This seems to work, I can now access the disk from Windows.

---

