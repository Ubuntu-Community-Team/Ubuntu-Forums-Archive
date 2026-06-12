---
title: "dd over usb external drive - damn automount!"
date: 2011-08-02
forum: General Help
---

### Post by esagherardo on 2011-08-02
I have an external harddisk (actually removed from a laptop) and I want do some analysis and data recovery on it. I bought a sata-to-usb adapter. 

Now the problem is: if I deselect media_automount "media_automount_open" and I select "media_autorun_never", the external sata driver is not recognised and I have no /dev/sdb1 to manually mount. Not a  hint of a newly plugged drive in dmesg.

Then I re-enabled automount and then I remounted the drives as read-only. Afterward I starter cloning the hd with dd.

After some three hours, the f*ck*ng laptop remounted the partition rw and the dd process went into io error.

So the question is: how can I safely work with a usb device with manual operations?  

Thanks a lot in advance for any help!

---

### Post by cipherboy_loc on 2011-08-02
Try unmounting it from the command line first (and waiting a bit):

```

sudo umount /dev/sdb1

```


BTW, when you say automount, what do you mean? Do you mean mountall, or the automatic disk mounting in Nautilus/GNOME.


Cipherboy

---

### Post by esagherardo on 2011-08-02
> **cipherboy_loc said:**
> Try unmounting it from the command line first (and waiting a bit):


That's what drives me mad: if I do that, the special files /dev/sdb* disappear!!

> 
BTW, when you say automount, what do you mean? Do you mean mountall, or the automatic disk mounting in Nautilus/GNOME.


Nautilus/gnome. 

My fstab is minimal:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

```

---

### Post by psusi on 2011-08-02
It sounds like your usb adapter is fubar.  It should not be disconnecting when you unmount the drive from the command line, and it sounds like during your dd transfer, it conked out, disconnected, and reconnected, causing it to be remounted and dd to error.

---

### Post by dcstar on 2011-08-03
> **psusi said:**
> **It sounds like your usb adapter is fubar**.  It should not be disconnecting when you unmount the drive from the command line, and it sounds like during your dd transfer, it conked out, disconnected, and reconnected, causing it to be remounted and dd to error.

Yep, or the USB ports are sus or cannot provide enough power.

I have never had problems like that doing disk to disk image copies using Ubuntu with external USB drive caddys - some of these take 10 hours!

I also never just use dd - **ddrescue** gives progress counts as well as taking bad blocks into account without aborting.

---

### Post by jmore9 on 2011-08-03
I have an laptop hard drive installed in an usb converter box and i just plug it in to the usb port and it treats it just like a regular hard drive.

I got 2 of those usb boxes for laptop hard drives for 3.99 on amazon about a year ago.  They can go up to a 500 gig drive.

Maybe that helped maybe not so much

---

