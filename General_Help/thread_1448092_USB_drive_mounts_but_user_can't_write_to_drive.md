---
title: "USB drive mounts but user can't write to drive"
date: 2010-04-06
forum: General Help
---

### Post by keithpeter on 2010-04-06
Hello All

I've got a bare bones Ubuntu 10.04 set up (xorg, openbox, usbmount). My (vfat32) stick drive mounts, and I can see what is in the one directory on the drive, but I can't write to the drive unless I use sudo. I tried the obvious step of attempting to change permissions on the drive..

```
keith@quiet:~$ sudo chmod -R 777 /media/usb0
[sudo] password for keith: 
keith@quiet:~$ ls /media/usb0
stuff
keith@quiet:~$ touch /media/usb0/readme.txt
touch: cannot touch `/media/usb0/readme.txt': Permission denied
```

I've seen these posts and they seem to relate to different situations...

[http://ubuntuforums.org/showthread.php?t=1445805&highlight=USB+drive+permissions](http://ubuntuforums.org/showthread.php?t=1445805&highlight=USB+drive+permissions)

[http://ubuntuforums.org/showthread.php?t=1434702&highlight=usbmounts+but+I+get+no+permissions&page=2](http://ubuntuforums.org/showthread.php?t=1434702&highlight=usbmounts+but+I+get+no+permissions&page=2)

Any ideas?

PS do we need a prefix for command line type systems?

---

### Post by nothingspecial on 2010-04-06
Try ```
sudo chown -R keith:keith /media/usb0
```

---

### Post by Morbius1 on 2010-04-06
You can't chmod or chown a FAT32 or NTFS formatted partition. That's for linux filetypes.

The real question is why is your USB stick mounting with owner = root. It should automount with owner = keith unless Ubuntu reset the defaults again in 10.04. 

Do you have an entry in fstab for this device. If so post the contents:

[B]cat /etc/fstab

[/B]You also might want to post the output of[B] sudo blkid
[/B]

---

### Post by keithpeter on 2010-04-06
> **nothingspecial said:**
> Try ```
sudo chown -R keith:keith /media/usb0
```

Thanks for reply, but...

```
chown: changing ownership of `/media/usb0/stuff/dttls': Operation not permitted
chown: changing ownership of `/media/usb0/stuff': Operation not permitted
chown: changing ownership of `/media/usb0': Operation not permitted
```

fdisk -l gives...

```
Disk /dev/sdd: 2057 MB, 2057306112 bytes
255 heads, 63 sectors/track, 250 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000336de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         250     2008093+   b  W95 FAT32
```

cat /etc/fstab gives just the root, home and swap partitions, no entry for USB as I was sort of expecting there not to be. Would adding an fstab entry help?

---

### Post by keithpeter on 2010-04-06
> **Morbius1 said:**
> You can't chmod or chown a FAT32 or NTFS formatted partition. That's for linux filetypes.

Do you have an entry in fstab for this device. If so post the contents:

[B]cat /etc/fstab

[/B]You also might want to post the output of[B] sudo blkid
[/B]

Thanks Morbius1, I've just seen your post. As mentioned above, no fstab for the USB stick. sudo blkid gives

```
/dev/sda1: UUID="87601e96-9320-42a5-bb2b-97ecb57ebf54" TYPE="ext4" 
/dev/sda5: TYPE="swap" 
/dev/sda6: UUID="ba78a906-a012-4f20-8cda-8d7332ec4b14" TYPE="ext3" 
/dev/sdd1: UUID="3C52-C8C5" TYPE="vfat"

```

I've been searching forums and there appear to be reports of defaults changing. System was installed and updated last night.

---

### Post by Morbius1 on 2010-04-06
You can add an entry but for the life of me I don't understand why it's necessary. Some developer somewhere didn't dot an "i" or cross a "t".

Anyway, to add an entry into fstab it would go something like this:

Open **Terminal**
Type **sudo mkdir /media/usbstick**
Type [B]gksu gedit /etc/fstab
[/B] 
Add an entry that looks like this:
```
 UUID=3C52-C8C5 /media/usbstick vfat user,umask=000,utf8,flush,noauto 0 0
```The "user" and "noauto" will allow the user to mount the device automatically when inserted.

The "umask=000" will allow read / write access to everyone.

When you're done, save fstab, exit gedit, and back in the Terminal type:
**sudo mount -a**

Then insert the stick and find out if I'm full of hooey ;)

---

### Post by keithpeter on 2010-04-06
> **Morbius1 said:**
> 

Then insert the stick and find out if I'm full of hooey ;)

You are right out of hooey;). Thanks very much.

```
keith@quiet:~$ touch /media/usbstick/stuff/great.txt
keith@quiet:~$ ls /media/usbstick/stuff
dttls  great.txt
```

Now, do I have to do this for each different drive that I use, so each one has a different UUID? 

Before I mark this as 'solved' has anyone got any ideas as to a 'general' solution that will get me back to where I am on another box with usbmount ('just works' with all permissions)?

Thanks all

---

### Post by Morbius1 on 2010-04-06
> Now, do I have to do this for each different drive that I use, so each one has a different UUID? Yes. I mean you could have done it this way:
```
 /dev/sdd1 /media/usbstick vfat user,umask=000,utf8,flush,noauto 0 0
```And if you only have one usb storage device this might work. But if you have many and they're formatted in NTFS, ext3, .... then you start getting into problems.

But as you stated above this is a workaround not a solution. Something's not right here.

---

### Post by keithpeter on 2010-04-06
> **Morbius1 said:**
> 
But as you stated above this is a workaround not a solution. Something's not right here.

I'll do a bit more searching and then post about it on the Lucid development forum and search launchpad later on. I'm hoping its a short term beta release issue and that the behaviour will return to normal for Lucid release.

The 'workaround' is helping me back up work for now, so I'm marking this as solved.

---

### Post by Scotus on 2010-04-15
This issue cropped up in 9.10 after the last update too

---

### Post by pregiopomo on 2010-05-23
I've been having the same problem for a while, and I went for the  solution posted here (modyfing the etc/fstub) then I finally went to  test it with the laptop of a friend that recently installed Ubuntu  10.04, and on his computer everything worked fine.

So I checked out the Synaptic packages he had installed by default, and I  realized that I had some more that probably were creating some  conflicts/problems.

Now it works again!!

Here is what i did:

- start the "synaptic package manager"
- insert "usb" in the quick search
- compare your installed packages with the following list (these are the  one installed by default):
:arrow: 
 usbmuxd
    usbutils
      libusbmuxd1
      libusb-0.1-4
      libusb-1.0-0
      xserver-xorg-video-sisusb
      libmtp8
      usb-creator-gtk
      usb-creator-common
      libmobiledevice0
      libgphoto2-port0
      libgphoto2-2
      media-player-info
      libhpmud0
      hpijs
      hplip
:arrow:
- remove those packages that have been added by you or that may cause  conflicts, in my case I had all the previous ones and I removed the  following that I added months ago messing up with my laptop:

     :arrow: 
usbmount  (yep it sound weird, but now is working properly in my  laptop!)
       pyton usb
       usb creator
       gnome pilot
:arrow:

I hope this example might help some people as I did receive help reading  this forum, this is not "THE WAY" you "HAVE TO" follow to solve this  problem, but this is just a way that worked for me, and I think is worth  to be shared :wink:

---

### Post by Anxiety35 on 2010-06-03
My friend was having this issue and the solution was just removing the "usbmount" package. That fixed everything instantly.

---

