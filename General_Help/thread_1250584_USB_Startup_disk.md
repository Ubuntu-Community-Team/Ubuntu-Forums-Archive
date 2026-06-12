---
title: "USB Startup disk"
date: 2009-08-26
forum: General Help
---

### Post by Xmister on 2009-08-26
Hi!
I have a 16GB pen drive.
I installed ubuntu 9.04 on it using the usb startup disk creator and choosed 5GB for storing settings.
But after every reboot, all the settings are gone. Users, Languages, everything.
I would like it to be non-persistent.
Could anyone help me? Thanks

---

### Post by coldReactive on 2009-08-26
> **Xmister said:**
> Hi!
I have a 16GB pen drive.
I installed ubuntu 9.04 on it using the usb startup disk creator and choosed 5GB for storing settings.
But after every reboot, all the settings are gone. Users, Languages, everything.
I would like it to be **_non-persistent_**.
Could anyone help me? Thanks

To keep your settings, files, etc. you *want* a **_persistent_** install.

---

### Post by P4man on 2009-08-26
I read about a bug with USB creator not making persistent sticks if they are larger than 4? GB. Not sure if its fixed meanwhile. 

Also I believe even on a persistent stick, the "ubuntu' user is recreated each boot, so you need to make another user to preserve your settings

---

### Post by Xmister on 2009-08-26
Thanks for the replies.
So, I want a persistent install.
And I tried to create a new user, but after the next reboot, that user gone too.
So, it's a bug in creator? If so, how could I make it persistent?

---

### Post by P4man on 2009-08-26
this should help:
[http://ubuntuforums.org/showpost.php?p=7161401&postcount=15](http://ubuntuforums.org/showpost.php?p=7161401&postcount=15)

however, since you got such a large stick, I would consider doing a full install to that stick, same way you install to a hd. It will take more space, but boots considerably faster and you got no live session weirdness. 

It will also boot just fine on just about any PC. I made one that way and even included nVidia binary drivers on it, with a little script that only loads them on a machine with an nvidia card. Works like a charm on 4 or 5 machines I tried it on.

---

### Post by Xmister on 2009-08-27
I tried but, I can't format the partitions on it, just to fat32, and simple ext2. Other file systems won't mount.

---

### Post by Mighty_Joe on 2009-08-27
> **P4man said:**
> I read about a bug with USB creator not making persistent sticks if they are larger than 4? GB. Not sure if its fixed meanwhile. 


[This bug]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") is confirmed but unassigned.

[QUOTE=Xmister]I tried but, I can't format the partitions on it, just to fat32, and simple ext2. Other file systems won't mount. [/QUOTE]
Exactly what did you try?  Gparted?  Command line?  What errors did you get?
I use ext2 with my flash drives.  It is believed that the extra writes in a journaling filesystem cause extra wear on a flash drive (I don't know if it's true, just one of those magical things we do).
Have a look at my post in [this topic]("http://ubuntuforums.org/showthread.php?t=1193680").  There's links to the install and configuration instructions I use.

---

### Post by Xmister on 2009-08-27
I tried ext3, ext4, xfs. With gparted, fdisk and with the installer too.
None of them worked.
Tried all the space in 1 partition and more partitions too.

---

### Post by Mighty_Joe on 2009-08-28
> **Xmister said:**
> 
None of them worked.


Exactly what does this mean?  You couldn't create a partition?  You couldn't install to that partition?  You couldn't boot from the install?
As I mentioned before, I and many others use ext2, which apparently does work for you, so why not use it?

---

### Post by Xmister on 2009-08-28
I can create and format the partition, but cannot mount.
And sadly the basic ext2 doesn't good for the installer, it wants it with "has_journal" and some other options, which way the partition - again - cannot mount.
I think the error is in the pendrive itself, so I will send it back, and buy a new one.
Anyway thanks for the help.

Notice:
The USB startup disk creator in 9.04 only creates persistence file system if you are copying the files from an iso image, not from a cd-rom! This way it worked for some time, I could boot into pendrive, and make changes, but now I cannot boot into it, no matter I recreate it using the program or not.

---

### Post by Mighty_Joe on 2009-08-28
> **Xmister said:**
> I can create and format the partition, but cannot mount.

Are you trying to mount the partition that you installed the Live CD to (and booted from)?  I don't think it can be done.  I've created secondary partitions on Live USB drives and successfully mounted them.

> **Xmister said:**
> And sadly the basic ext2 doesn't good for the installer, it wants it with "has_journal" and some other options, which way the partition - again - cannot mount.

Again, are we talking about the Live CD installer?  The [documentation recommends ]("https://help.ubuntu.com/community/Installation/FromUSBStick") FAT32.

> **Xmister said:**
> 
The USB startup disk creator in 9.04 only creates persistence file system if you are copying the files from an iso image, not from a cd-rom! 

I'm not sure what you are claiming here.  You cannot create a persistent Live USB drive from the Live CD? I've done it several times.  If you really think there's a bug, report it in Launchpad.

> **Xmister said:**
> 
This way it worked for some time, I could boot into pendrive, and make changes, but now I cannot boot into it, no matter I recreate it using the program or not.

There's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702") where casper-rw is not cleanly unmounted on shutdown.  That could explain your problem.

---

### Post by Xmister on 2009-08-28
> **Mighty_Joe said:**
> Are you trying to mount the partition that you installed the Live CD to (and booted from)?  I don't think it can be done.  I've created secondary partitions on Live USB drives and successfully mounted them.

No. I'm talking about that, if I format a partition on the drive using ext3, then this partition cannot mount(no valid journal found, bad superblock).


> **Mighty_Joe said:**
> I'm not sure what you are claiming here.  You cannot create a persistent Live USB drive from the Live CD? I've done it several times.  If you really think there's a bug, report it in Launchpad.
If I try to create directly from the CD, the casper-rw file wouldn't be created. If I'm doing it from an ISO image, the file will be created.



> **Mighty_Joe said:**
> There's a [known bug]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/125702") where casper-rw is not cleanly unmounted on shutdown.  That could explain your problem.

Yeah, but I tried to reformat, and recreate the boot usb, using usb startup disk creator, and still cannot boot.

The first time I created the boot usb, it started, and I could use the usb system. But after some reboot, the usb wouldn't boot. This time I tried to reinstall the system using the usb startupd disk creator with no luck. Still cannot boot.
And I've seen some I/O errors in logs while the system was running, so I think this really is a h/w problem.

EDIT(29.08):
I've found out that the first 2GB of blocks is OK on the device, I did successfully create and mount ext3 filesystem on it. But at around 3-4GB and after that I can't, and there are I/O Errors, so it really looks like a HW error.
I will send it back for a refund. Anyway, thanks for the help!

---

### Post by brunolabs on 2009-09-10
> **Xmister said:**
> Hi!
I have a 16GB pen drive.
I installed ubuntu 9.04 on it using the usb startup disk creator

How did you do that?
I keep getting the "USB drive not a boot drive" error message.
How can I make it bootable?

Thanks!

---

### Post by Mighty_Joe on 2009-09-10
> **brunolabs said:**
> 
How can I make it bootable?


The usb startup disk creator should make it bootable.  Try using [GParted]("https://help.ubuntu.com/community/HowtoPartition") to delete the existing partition(s) -back up existing data first!- create a primary partition and format it FAT32 and try the USB disk creator again.  
There's a known bug with the creator that it doesn't work unless the USB drive has a partition table, but it will not error out ([277865]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")).

---

### Post by brunolabs on 2009-09-12
> **Mighty_Joe said:**
> The usb startup disk creator should make it bootable.  Try using [GParted]("https://help.ubuntu.com/community/HowtoPartition") to delete the existing partition(s) -back up existing data first!- create a primary partition and format it FAT32 and try the USB disk creator again.  
There's a known bug with the creator that it doesn't work unless the USB drive has a partition table, but it will not error out ([277865]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/277865")).

Tried that. I get the same error. :(
No problem. It's not important. I just wanted to test booting from USB.

Thanks anyway. ;)

---

### Post by jimmers on 2009-09-12
I to have successfully installed jaunty on various 16 gig pendrives, I found the most successful ones are Sandisk Cruzer (works a treat) and Intregal, You can install to LG pendrives, but I could never get them to run, it cost me lots of time and dosh to find this out, and I ended up with a plethara of pendrives.
I tried using Unetbootin but it did'nt work, also when trying a complete install, I found that I had to re-install the complete OS on my machine.
But never mind that, the bottom line is that you can have a workable pendrive by using the USB Creator.



Jimmers

---

