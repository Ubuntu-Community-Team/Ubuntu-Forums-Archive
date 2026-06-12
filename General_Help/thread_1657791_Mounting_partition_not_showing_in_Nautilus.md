---
title: "Mounting: partition not showing in Nautilus"
date: 2011-01-01
forum: General Help
---

### Post by Aleksandar_B on 2011-01-01
Hi. Besides having Ubuntu I also have Windows 7 and to keep data between the two I keep a separate partition. So far I have been automatically mounting this partition in /media by editing fstab. The partition shows up in Places and on Desktop.

Now I have changed mount-point to be in /mnt and this works fine, the partition mounts. The problem is that it doesn't show up in Places nor on the Desktop. I have changed back the mount-point to /media and the partition shows up on the Desktop and in Places fine, but when the mount-point is changed it won't show up anymore.

Is there a solution to this problem?

---

### Post by TeoBigusGeekus on 2011-01-01
/mnt used to be the place where everything was mounted.
Today, all modern linux systems mount their volumes in the /media folder.
My guess is that it is an intrinsic nautilus setting to show everything mounted on /media (and /media only) and I don't think you could do much about it.

---

### Post by Aleksandar_B on 2011-01-01
From what I could gather, /mnt is for internal disks (permanent media) and /media is for temporary media (external disks, usb keys, cd/dvd media...).

I have just tried manually mounting my usb key to /mnt and It doesn't show up on desktop, while mounting it automatically mounts it in /media and it shows up on Desktop.

It's really strange, but I guess there must be a solution for this.

---

### Post by dcstar on 2011-01-02
> **Aleksandar_B said:**
> From what I could gather, /mnt is for internal disks (permanent media) and /media is for temporary media (external disks, usb keys, cd/dvd media...).

I have just tried manually mounting my usb key to /mnt and It doesn't show up on desktop, while mounting it automatically mounts it in /media and it shows up on Desktop.

It's really strange, but I guess there must be a solution for this.

There is no "solution" required, it is working **exactly** how it is supposed to work.

**You** either leave the system to mount removable devices as it is designed to, or **you** decide to mount them yourself and the system does not do what it previously did.

**You** decide which way you want the system to work.

---

### Post by garvinrick4 on 2011-01-02
If you mount a /dev in /mnt while it is mounted look in file system in /mnt it will be there.

---

### Post by Aleksandar_B on 2011-01-02
I think i have not made myself clear. I have no problem mounting partitions, the problem is that when they are mounted in some other location other than /media they do not show up on Desktop nor under Places. I know I could go into /mnt and access my data from a mounted partition from there but that is not very practical.

I have explored some situations and these are my results:

[LIST=1]
[*]Automatically (through fstab) mounting in /media: The partition get's mounted and it shows up on the Desktop and under Places in Nautilus.


[*]Manually (through Nautilus) mounting: The partition get's mounted in /media and shows up on the Desktop and under Places in Nautilus.


[*]Manually (through terminal) mounting in /media: The partition get's mounted in /media and shows up on the Desktop and under Places in Nautilus.


[*]Automatically (through fstab) mounting in /mnt: The partition get's mounted and in doesn't show up on the Desktop and under Places in Nautilus.


[*]Manually (by terminal) mounting in /mnt: The partition get's mounted and in doesn't show up on the Desktop and under Places in Nautilus.
[/LIST]

---

### Post by Aleksandar_B on 2011-01-09
As I have recently found out through further research, partitions mounted in /mnt will NEVER be visible on the Desktop or under Places. So it's either using /media or creating some other folder since any folder can be used as a mount point. 

This wasn't really a problem just something I noticed.

---

