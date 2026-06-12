---
title: "How to hide a harddrive?"
date: 2010-04-02
forum: General Help
---

### Post by everytimeref on 2010-04-02
I's a small problem, but I thought I'd ask about it anyway...

I have a second harddrive that mounts on startup and I use to store all my videos.

My problem is that although I want it to mount and appear in 'places' I don't really want it appearing on the desktop.

I've tried renaming it .Videos but the desktop doesn't obey that rule...

All the help I've found online has been how to hide all mounted drives. I really don't want to do that.

---

### Post by eksasol on 2010-04-02
The only way I know of is to hide the harddrives, then "Create Launcher" to a specific location on the desktop. When you create a launcher, make sure to choose:
Type: Location
Location: type down the address of the hdd, such as: /media/dirtyvideos

Then you have to choose an icon for that launcher, the default icons are located in: /usr/share/icons/gnome/scalable/devices/

Now if you want to hide harddrive completely from Nautilus, that's a different story. You can follow a guide from this user: [http://ubuntuforums.org/showpost.php?p=3474429&postcount=8](http://ubuntuforums.org/showpost.php?p=3474429&postcount=8)

---

### Post by Elfy on 2010-04-02
I assume that it mounts in /media - change fstab so that it mounts in /mnt 

or turn off showing any drives on the desktop - but that means that Cd or usb's you plug in do not show.

If for instance fstab has it mounting to /media/foo

make a directory 

```
sudo mkdir /mnt/foo
```

then change the fstab line to suit.

---

### Post by dcstar on 2010-04-03
> **everytimeref said:**
> I's a small problem, but I thought I'd ask about it anyway...

I have a second harddrive that mounts on startup and I use to store all my videos.

My problem is that although I want it to mount and appear in 'places' I don't really want it appearing on the desktop.

I've tried renaming it .Videos but the desktop doesn't obey that rule...

All the help I've found online has been how to hide all mounted drives. I really don't want to do that.

You can turn off the display of mounted external drives on your Desktop, is that what you want?

---

### Post by everytimeref on 2010-04-03
> **dcstar said:**
> You can turn off the display of mounted external drives on your Desktop, is that what you want?

No I just want to hide this one specific drive.

---

### Post by everytimeref on 2010-04-03
> **forestpiskie said:**
> I assume that it mounts in /media - change fstab so that it mounts in /mnt 

or turn off showing any drives on the desktop - but that means that Cd or usb's you plug in do not show.

If for instance fstab has it mounting to /media/foo

make a directory 

```
sudo mkdir /mnt/foo
```

then change the fstab line to suit.

I'll give this a try...

---

### Post by Elfy on 2010-04-03
> **everytimeref said:**
> I'll give this a try...
If you are unsure post your fstab - but it should be fairly simple to do.

You'll need to unmount the drive on the desktop - right click unmount and then remount it with 

```
sudo mount -a 
```

That should not appear to do anything - if it does say anything it will be an error.

---

### Post by everytimeref on 2010-04-26
I finally got a chance to try this (kids, job, building work etc.) and it has worked exactly as I want.

Thankyou very much forestpiskie!

---

