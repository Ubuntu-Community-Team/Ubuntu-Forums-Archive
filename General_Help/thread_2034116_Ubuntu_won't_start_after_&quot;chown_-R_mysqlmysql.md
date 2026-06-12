---
title: "Ubuntu won't start after &quot;chown -R mysql:mysql /&quot;"
date: 2012-07-27
forum: General Help
---

### Post by myralfa on 2012-07-27
Yes, I'm that stupid.
I was setting up a MySQL server, and when running it, and error promted telling me that mysql was denied to access certain files. So in an attack of lazyness instead of giving permission or giving ownership over those files, I put "chown -R mysql:mysql /". Obviously the second after I hit enter I knew that I f*cked up. Normally I would reinstall, but this time I can't. I need access to the file system to recover some files.
When trying to boot on recovery mode, the computer freezes displaying this message (been over an hour in that state):
Loading Linux 3.0.0-17-generic ...
Loading initial ramdisk ...
And when trying to boot normally the screen starts loading the Ubuntu loadscreen (the one with the white and orange balls) and then goes black displaying this:

*Starting web server apache2   [OK]
We do not own /var/log/pm-powersave.log, refusing to overwrite.
   Checking battery state... [OK]
*Starting CUPS printing spooler/server  [OK]
####empty line, but at the end there is a "U"
nhandled kernel version: 3.0 ('uname -r' = '3.0.0-17-generic')
Couldn't aquire lock. Retrying....
Unhandled kernel version: 3.0 ('uname -r' = '3.0.0-17-generic')
*Enablin
g laptop mode... [OK]
*Stopping System V runlevel compatibility [OK]

Typed exactly as appears in the PC. Maybe it can help.
So, bottom line is, I need some of the files in there, any way to access them?

Edit: Running Ubuntu 11.10

---

### Post by LiamOS on 2012-07-27
If you have a live CD/USB lying about, boot that up. Set yourself up as root in the live environment and mount your partitions. 

If you're unfamiliar with this, the way to go is(I'm assuming a live Ubuntu environment):

Get yourself set up as root, to speed things along:
$ sudo passwd root
$ su -

Then make yourself some mountpoints:
# mkdir /mnt/ubuntu (You can use whatever directory name you want.)
# mount /dev/sda3 /mnt/ubuntu (If /dev/sda3 is your root partition, if not substitute what's appropriate.)
Then mount any other partitions to their respective points if you need to, e.g.
# mount /dev/sda1 /mnt/ubuntu/boot (If /dev/sda1 is your boot partition.)

Now you can browse through your files and copy them over to an external hard drive, flash drive or whatever. 



Also, I've never tried it, but you could possibly
$ sudo nautilus
and use that to recover your files, as nautilus *may* do the necessary mounting for you.

---

### Post by myralfa on 2012-07-27
I'll make a live usb and try that. Thanks for the reply.
Gona report back in a while.

---

### Post by myralfa on 2012-07-27
Any way to figure which was my root & boot partition? My root one isn't sda3

Edit: mounted sda1 but appears to be the windows one. And when I try to mount the sda2 (mount /dev/sda2 /mnt/ubuntu2 ) y get:
mount: you must specify the filesystem type

Second edit: Solved it using fdisk -l I now have access to the old file system. Thanks a lot.

I really don't know if I should tag the thread as solved, because I solved only the part of accessing the data, not the OS per se.

---

### Post by Cheesehead on 2012-07-27
It will probably be easier for you to recover your data, then reinstall.
Looking up the correct permissions on thousands of files and directories, then manually fixing each one does not sound like a fun hobby.

---

