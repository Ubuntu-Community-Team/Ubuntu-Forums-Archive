---
title: "Hotpluging SATA and eSATA drives"
date: 2011-10-04
forum: General Help
---

### Post by zero2xiii on 2011-10-04
Hay all,

I have this external 1TB drive with eSATA. It is hotplugable but when I plug into my computer (ubuntu 10.04_32) and into my laptop (ubuntu studio 10.04_64) it is not detected or mounted (It has 2 partitions equal in size).

How can I mount this drive if it is plugged in AFTER boot, I really dont want to reboot the PC each time I add or remove the drive.

Thanks

---

### Post by dino99 on 2011-10-04
maybe you need to log out/in

[https://wiki.ubuntu.com/X/InputHotplug](https://wiki.ubuntu.com/X/InputHotplug)

---

### Post by seawolf167 on 2011-10-04
+1 for dino99's post, though it seems to me that I haven't had to relog with my eSata external hard drive in 10.04 LTS. If it still isn't auto-mounting, you can manually mount it following [these instructions]("https://help.ubuntu.com/community/Mount")

---

### Post by zero2xiii on 2011-10-05
Hay,

Seems like I haven't given enough information about my issue.

I tried the loging out and then back in. No luck.

The drive is not picked up at all if it is connected after boot. Not with gparted, or disk utility. So I cannot run something like:

```
sudo mount /dev/sdb1 /Multimedia
```

only as an example.


But after a reboot, the drive is picked up normaly and I can mount it by going to Places and the clicking on the drive partition I wish to mount.


I have read elsewhere on the internet there is a BIOS option that depicts if a sata device is detected when it is hotpluged, or only during startup. Is this true? Should I be looking at hardware level rather than software level?

Thanks a lot :)
Cherz

---

### Post by seawolf167 on 2011-10-05
You have initialized and partitioned your disk, correct? If not, do that, then keep reading.

In BIOS (hit [F2] during POST to enter BIOS), check for the hard drive mode - you should have it set to ACHI (versus IDE or RAID). Save your changes and reboot, then try to see if it works properly.

---

### Post by dino99 on 2011-10-05
such kind of job is normally done via the "mountall" package

sudo apt-get install --reinstall mountall

and your /etc/fstab might be similar than mine :

proc /proc proc defaults 0 2
UUID=5d8d1ee1-f5af-40a1-a45d-dbc570808523 /home ext3 defaults,relatime 0 2
UUID=0a9ca7f0-6eeb-4b21-b70f-670fa600de16 none swap sw 0 0

as you see, it is minimalist: only /home & swap partitions, dont need more.

---

### Post by zero2xiii on 2011-10-05
> check for the hard drive mode - you should have it set to ACHI

AAAAH that worked!.. Thanks. Now the drive is detected correcly (partitions and all) as I expect it to.. Exactly the same way as it is if it is attached before boot.

Thanks for all the help guys (or girls lolz)

Cherz

---

### Post by seawolf167 on 2011-10-05
Awesome :) glad all is working now!

---

