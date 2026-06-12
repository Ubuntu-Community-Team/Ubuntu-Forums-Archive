---
title: "USB MINT 7 install to hard drive from USB??"
date: 2009-06-25
forum: General Help
---

### Post by jake16424 on 2009-06-25
Haven't had much luck installing to a EXT4 partition.

don't have a father file system atm to do dual boot, i want to install linux as primary OS and use WINE\Virtualbox both of which are configured and able to run right now. 

how do i install linux from my usb to the designated hdd?

---

### Post by loomsen on 2009-06-25
I never ran mint, but I guess you have a live image?
It should include a installer, Make a boot partition (100MB of size are far enough if you use to keep your computer clean, if you're a messie make it 500 or so) 
FS=ext3 (I guess you don't want to know how to make grub boot ext4, btrfs, whatever, do you?) If you wanna go a little more into the detail, /boot will hold around 4MB-20MB sized files, so chosing an appropriate blocksize during partitioning won't do any harm (actually, it holds a kernel image = vmlinuz and a initial ram disk = initrd or initramfs)

The initrd/initramfs is copied to RAM, then your hardware will be populated from there. So if you wanna make grub boot ext4 you need a initrd.img including the ext4 module, but this exceeds your question I think.

OK, back 2 topic, 
/boot 250MB, ext3,noatime,nodiratime 
/     <4-15GB> depending on your needs, FS is pretty much up to you
/home <as big as you want> FS again up to you, here is where you should be all the time, your media, your temp files, your private files, everything you basically do with your PC. A separate /home is very useful as /home holds the users configurations. So, if you ever happen to reinstall you may simply mount your /home into your new OS (or share it between multiple OS' or or or :) )

This is basically enough to get you going.
[ I've got a couple partitions more, up to you/your needs]

---

### Post by jake16424 on 2009-06-25
someone mark this as solved.

use the USB flash drive as LIVE CD and format previously the hdd in question and install to the whole thing =D

---

### Post by jake16424 on 2009-06-25
> **loomsen said:**
> I never ran mint, but I guess you have a live image?
It should include a installer, Make a boot partition (100MB of size are far enough if you use to keep your computer clean, if you're a messie make it 500 or so) 
FS=ext3 (I guess you don't want to know how to make grub boot ext4, btrfs, whatever, do you?) If you wanna go a little more into the detail, /boot will hold around 4MB-20MB sized files, so chosing an appropriate blocksize during partitioning won't do any harm (actually, it holds a kernel image = vmlinuz and a initial ram disk = initrd or initramfs)

The initrd/initramfs is copied to RAM, then your hardware will be populated from there. So if you wanna make grub boot ext4 you need a initrd.img including the ext4 module, but this exceeds your question I think.



OK, back 2 topic, 
/boot 250MB, ext3,noatime,nodiratime 
/     <4-15GB> depending on your needs, FS is pretty much up to you
/home <as big as you want> FS again up to you, here is where you should be all the time, your media, your temp files, your private files, everything you basically do with your PC. A separate /home is very useful as /home holds the users configurations. So, if you ever happen to reinstall you may simply mount your /home into your new OS (or share it between multiple OS' or or or :) )

This is basically enough to get you going.
[ I've got a couple partitions more, up to you/your needs]

my eyes glazed over after the second paragraph...

i have a clean hdd i formatted it to EXT4 or whatever that is.

its installing now so no worries, thank you for your help though!

these forums are pretty helpful and welcome places for newbies like myself =-D

---

### Post by jake16424 on 2009-06-25
Now that i have installed Linux, and i have a Persistant install on my USB

can i transfer the things i have done on my Persistance USB OS to the new not in use yet file system of the hard drive install

---

### Post by loomsen on 2009-06-25
> the things i have done

Depending on what things you figure to do ^^

Create yourself a user profile and use some handy tool to have it synced with a user account on your Computer for instance. 
Take a look at rsync or sth similar.

> can i 

The only limit in linux is set by the user using it.

---

### Post by jake16424 on 2009-06-25
> **loomsen said:**
> Depending on what things you figure to do ^^

Create yourself a user profile and use some handy tool to have it synced with a user account on your Computer for instance. 
Take a look at rsync or sth similar.

huh?

all i want to do is transfer my profile or whatever has all the things i have installed over to my fresh install of linux on my hard drive from my flash drive.

---

### Post by loomsen on 2009-06-25
Yep, and I told you how.

Make a separate /home partition and you'll never ever lose any settings anymore.

> 
 has all the things i have installed

A common application usually consists of more than one part. You install the app (== providing any functionality AND settings/customization options)
The second part is what happens in your /home/ME/ directory. Every setting you make is saved to $HOME

This means, lets say you mounted your $HOME to a newly installed system, you only need to pull in the binary, and BAM! It will look just like you'd never have changed anything. 

You may know, linux is modular... So most apps are configured to look into different places for settings, usually allowing the USER to override defaults. And this applies to nearly every application you can change at least one setting. This has to happen inside your $HOME cause you don't have write permissions anywhere else, and that's good!

Concrete: (assuming hd sda and flash drive sdb)
```

su -l 
adduser foobar
mkdir /mnt/sdb && mount /dev/sdb1 /mnt/sdb
## -- cp -r /mnt/sdb/<path-to-home-dir> /path/to/just/created/home/dir  -- ##
## for example
cp -r /mnt/sdb/home/foobar/* /home/foobar
chown -R foobar:foobar /home/foobar
exit

```

Now log in as foobar, and you should have just the same settings as on your stick

---

### Post by omar.shraim on 2009-08-23
Just thought to share this great site dedicated to "Boot and run Linux from a USB flash memory stick". The site has automated detailed steps to the same for most known Linux distros. There is one for Mint 7 but the steps are for doing it from inside windows. Still, I managed to do it and it was a breaze. :popcorn:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

