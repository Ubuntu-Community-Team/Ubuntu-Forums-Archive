---
title: "Change ipod mount point /media/sde -&gt; /media/ipod?"
date: 2006-03-04
forum: General Help
---

### Post by garton on 2006-03-04
I have a problem with amarok and my ipod. When I plug the ipod in, it is detected perfectly and KDE mounts it automatically... the problem is that it gets mounted at /media/sde2, where amarok can't find it.

If I manually umount the ipod and remount it at /media/ipod, amarok detects it and the ipod amarok plugin gets launched. 

So, I assume that somewhere I can configure the mount point for my ipod, but I cannot find out where! It's certainly not in /etc/fstab, but instead buried deep within some arcane hotplug-HAL-thingamajig.

Any ideas? Thanks.

Oh, and I'm running Dapper with amarok and libgpod built from soruces, not the versions in the repositories.

---

### Post by Rizado on 2006-03-04
A quick fix would be "ln -s /media/sde2 /media/ipod" or you could just umount it and remount or add it to fstab.

---

### Post by aysiu on 2006-03-04
Why not just add it to your /etc/fstab? Add this line in ```
/dev/sde2 /media/ipod vfat umask=000 0 0
```

---

### Post by nrwilk on 2006-03-04
[QUOTE=aysiu]Why not just add it to your /etc/fstab? Add this line in ```
/dev/sde2 /media/ipod vfat umask=000 0 0
```[/QUOTE]
Or, if it has previously been used on a Mac, it will be this instead:
```

/dev/sde2 /media/ipod hfsplus umask=000 0 0

```

---

### Post by WurdahMekanik on 2007-11-08
what if my ipod doesn't always mount to the same place and i want it to always show up under /mnt/ipod?

for example: if i boot up with the pod connected it will mount to sdb or sdc (depending on other devices i have connected), but if i boot up and then connect the pod, or umount/disconnect the pod and umount/connect/disconnect other devices and then reconnect the pod it will go to sdf or sdg or something...

i know there is a way for it to always mount to /mnt/ipod considering that slackware asks if i want to set a mount point for my devices during the install, and i've successfully set it to always mount to /mnt/ipod with that

---

### Post by dcstar on 2007-11-08
> **WurdahMekanik said:**
> 
...........
i know there is a way for it to always mount to /mnt/ipod considering that slackware asks if i want to set a mount point for my devices during the install, and i've successfully set it to always mount to /mnt/ipod with that

The simplest way is to give the iPod partition a label, then it will **always** be mounted at /dev/LABEL.

This works with all USB external partitions.

---

### Post by andersja on 2008-01-06
> **dcstar said:**
> The simplest way is to give the iPod partition a label, then it will **always** be mounted at /dev/LABEL.

This works with all USB external partitions.

I accidentally set my label in the GNOME GUI as /media/something and I connect my ipod now I get an error message that the label name has a directory separator in it. Where are labels stored? I checked fstab already?

---

### Post by soxs on 2008-02-05
*removed* *missunderstanding*

---

