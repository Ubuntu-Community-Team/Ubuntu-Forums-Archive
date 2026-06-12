---
title: "I edited swap partition and now things are strange"
date: 2009-11-24
forum: General Help
---

### Post by winchendonsprings on 2009-11-24
Okay, heres the turn of events.

1. I booted from live cd to reduce my swap partition size.

2. I entered gparted partition manager.

3. turned off swap.

4. reduced it from 16.07 GB to 10 GB

5. moved the resized swap partition to the right edge.

6. enlarged the regular ext3 partition with ubuntu on it, to take up the 6.07 GB left over from the swap decrease.

All this took about 15 minutes and then I rebooted the computer normally. When I choose my most current kernel 2.6.31 -15 there is an error saying a partition has not mounted - swap, then it loads a completely white desktop. here is the screenshot. no wallpaper, no panel. everything still works, but, well, its all white. see first screenshot.

BUT if I start up from the second kernel in the grub menu 2.6.31-14. everything appears to be fine. This is how it should look. the second screenshot. also there is no sound.

SO, WHAT SHOULD I DO? go back to the live cd and enlarge the swap partition? or will that damage it more? any ideas?

[IMG]http://lh5.ggpht.com/_IW9lx8xoDpo/SwxsbseOnmI/AAAAAAAAAcM/6tSfoA-X1V4/s1280/Screenshot.png[/IMG][IMG]http://lh6.ggpht.com/_IW9lx8xoDpo/Swxt_OEdMLI/AAAAAAAAAcU/-djoDA_RA3U/s1280/Screenshot-2.png[/IMG]
[IMG]http://picasaweb.google.com/lh/photo/cWXvaU_ySD4swnnFHRzZ8w?authkey=Gv1sRgCNbM7pP-7YvusAE&feat=directlink[/IMG]

---

### Post by dcstar on 2009-11-24
> **winchendonsprings said:**
> Okay, heres the turn of events.

1. I booted from live cd to reduce my swap partition size.

2. I entered gparted partition manager.

3. turned off swap.

4. reduced it from 16.07 GB to 10 GB

5. moved the resized swap partition to the right edge.
........

Double-check the UUID of the swap partition and the corresponding setting in the /etc/fstab file.

You also need to verify that the swap is actually enabled:

```
sudo swapon -s
```

---

### Post by winchendonsprings on 2009-11-25
the UUID of the swap I get from, blkid, and the one in the fstab file are definitely not the same.

should i change the fstab file?

---

### Post by winchendonsprings on 2009-11-25
Well, David, I changed the UUID of the swap partition in the fstab file to match the UUID of the swap partition i see in blkid and gparted. and ..... All seems back to normal!

Thanks a lot! lifesaver

---

### Post by slakkie on 2009-11-25
You could also use /dev/$something instead of the UUID.
That way you'll never have problems when resizing your partitions.

---

### Post by winchendonsprings on 2009-11-25
just simply /dev/$something where the UUID number is in the fstab file?

---

### Post by slakkie on 2009-11-25
> **winchendonsprings said:**
> just simply /dev/$something where the UUID number is in the fstab file?

Yes, for example my fstab under Debian, this will also work on Ubuntu:

```

/dev/sda3       /               ext3    errors=remount-ro   0       1
/dev/sda1       /mnt/boot       ext3    defaults        0       1
/dev/sda9       /home           ext3    defaults,errors=remount-ro 0       2
/dev/sda8       /opt            ext3    defaults        0       2
/dev/sda7       /var/log        ext3    defaults        0       2
/dev/sda6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

This will work just as with the UUID.

---

### Post by dcstar on 2009-11-25
> **slakkie said:**
> 
..........
This will work just as with the UUID.

Until you plug in some more hardware and the /dev/ designation changes.

UUIDs are used to insulate the system from any device designations, which can be arbitrary and change on each bootup.

---

