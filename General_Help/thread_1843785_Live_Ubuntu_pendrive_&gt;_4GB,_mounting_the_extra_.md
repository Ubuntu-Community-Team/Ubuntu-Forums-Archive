---
title: "Live Ubuntu pendrive &gt; 4GB, mounting the extra space as /home dir, is it possible?"
date: 2011-09-14
forum: General Help
---

### Post by deckoff on 2011-09-14
So.
I have a company PC. - I am not allowed to wipe the XP from it
I have 16GB pendrive. I split it, I boot without a problem, the second partition is mounted and seen OK.
I want it mounted on boot as at /home/ , I want to install Civ 5 on it. If the second part of the USB is mounted as USB, it is not allowed to start exe , sh files... So, I cannot install nothing on it. Since the game needs more than 3 GB, I cannot place it on my / partiton.
Adding the second partition into /etc/fstab, caused the drive not to boot the first time, and after a second try to boot from the USB, the changes were gone

---

### Post by 2F4U on 2011-09-14
I guess what you are looking for is a persistent usb drive installation. This article should help

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by deckoff on 2011-09-14
No. I l can easily make a live USB. Persistent USB cannot have more that 4GB space.
What I do usually is, if I have an USB lager that 4 GB, I split it into 2 parts. One I use for the actula live USB, the other one is empty - I usually use as normal USB. 
What I want is a way to mount this spare, empty partition on boot at /home/, so I can have more free space...

---

### Post by dcstar on 2011-09-15
> **deckoff said:**
> No. I l can easily make a live USB. Persistent USB cannot have more that 4GB space.
What I do usually is, if I have an USB lager that 4 GB, I split it into 2 parts. One I use for the actula live USB, the other one is empty - I usually use as normal USB. 
What I want is a way to mount this spare, empty partition on boot at /home/, so I can have more free space...

System partitions such as /home **must** be Linux filesystems.

AFAIK there is no reason why a Persistent USB should not use its /etc/fstab file as any "normal" system.

---

### Post by deckoff on 2011-09-15
Is there a way to make a live USB with more than 4GB persistent file? even with bigger USB, I cannot set the persistent file to be bigger than 4GB... I formatted the USB to fat32, have not tried with ext2 or native...

---

### Post by haqking on 2011-09-15
> **deckoff said:**
> Is there a way to make a live USB with more than 4GB persistent file? even with bigger USB, I cannot set the persistent file to be bigger than 4GB... I formatted the USB to fat32, have not tried with ext2 or native...

it is a limit of Fat32

see here for how to get around it

[http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

and 
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by deckoff on 2011-09-15
This explains lots of things, - most probably trying to boot home to a vfat ext forced ubuntu to fall to its default fstab. Will try, report and mark as solved if this helps :)

---

### Post by The Cog on 2011-09-15
Threads merged.

I think I would have created an ext2 partition for the spare space on the drive, and mounted that with its own entry in fstab. I haven't tried it, but that's the approach I would take.

---

