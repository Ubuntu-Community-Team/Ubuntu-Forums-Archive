---
title: "Can 'dd' be used to write an .iso to a USB to make a startup disk?"
date: 2010-02-22
forum: General Help
---

### Post by oppih on 2010-02-22
As the title ssaid, tonight I've tried to use the command 'dd' as UltraISO on my jaunty to write an .iso file to a USB disk to get it work to install a new system.
I know I can use 'dd' like this:
```
dd if= foo.img of=/dev/sdb
```
This does work on my PC,and I can use it to install ArchLinux.

Then, I want to write karmic's .iso file into my USB disk so I needn't burn a CD.
I know I can use other software to accomplish my task,but I still want to know.
When I search on Google,all I can only find is 'dd' being used with the '.img' filetype, not '.iso'.

But someone tell me that "The dd utility copies the standard input to the standard output. if=file Read input from file instead of the standard input. Whatever the data format is, dd can read data from it."

---

### Post by dandnsmith on 2010-02-22
It's true that dd can effectively copy anything - the problem is that the .img and .iso formats are different, so you don't get the end result you'd like.

Try investigating the mount command, and loop mount the .iso so you can 'see' the encoded filesystem. You should then be able to dd that filesystem to get something on your USB stick which you can use for installation.

---

### Post by oppih on 2010-02-22
Thank you for your answer~
Next I'll try to mount the .iso file as an device and then 'dd' it into my USB disk , right?

---

### Post by oppih on 2010-02-23
> **dandnsmith said:**
> Try investigating the mount command, and loop mount the .iso so you can 'see' the encoded filesystem. You should then be able to dd that filesystem to get something on your USB stick which you can use for installation.

I've learned how to mount the iso9660 file on /media/iso using these commands:
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso
```
Then I need to 'dd' it into my USB disk.What's the 'if' of 'dd'? Should I do it like this ?
```
sudo dd if=/media/iso of=/dev/sdb
```
Or I should use something in /dev such as 'loop' or 'loop1' ?
Thank you!

---

### Post by amsterdamharu on 2010-02-23
No dd won't work, try unetbootin or after mounting the iso copy all the files to usb and make the usb bootable with syslinux (most cd's use isolinux). Rename isolinux.conf to syslinux.conf.

This doesn't allways work since some distros will look for CD rom during startup.

---

### Post by oppih on 2010-02-23
All I want to do is to find an easy way to make a bootable USB disk that contains Ubuntu 9.10 and then I could use it for installation...

---

### Post by amsterdamharu on 2010-02-23
Install unetbootin that will do.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oppih on 2010-02-23
Good~ I got it!

Thank you ~ UNetbootin is the very software I need !

---

