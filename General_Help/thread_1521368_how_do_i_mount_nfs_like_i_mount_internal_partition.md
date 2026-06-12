---
title: "how do i mount nfs like i mount internal partition?"
date: 2010-06-30
forum: General Help
---

### Post by gothxx on 2010-06-30
I want to connect to the nfs in the same way i mount "29GB filesystem" in "Places".

I know how to mount with fstab, but then they are always mounted and i cant unmount them as not root(suppose it's because i don't use terminal and sudo).

Now fstab looks like 192.168.0.250:/mnt/data0/tv-series /home/username/NAS/tv-series nfs rsize=8192,wsize=8192,timeo=14,intr

Also , it seems like I only have read permission, how do I change it?

And finally as a bonus question, is there any way to use elevated privileges using graphical interface?

Sorry if it's not understandable.

---

### Post by skullmunky on 2010-06-30
for the fstab options, take a look at [https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

adding user,rw to the options should let you mount/unmount as a regular user, and have it read/write:

```

192.168.0.250:/mnt/data0/tv-series /home/username/NAS/tv-series nfs rsize=8192,wsize=8192,timeo=14,intr,user,rw

```

but that's a good question, how to make it mountable/unmountable through the Places menu, or Nautilus, or Dolphin, etc.  I don't know whether those use fstab, or udev, or some other system to decide what to put there...

---

### Post by gothxx on 2010-07-01
Thanks, but it does not seem to work...

Still says that only root can unmount, and I do not have permission to "create in that location"

Now two out of the 4 has networkfolder apperance and those folders launch automatically when I start the computer... strange....

---

