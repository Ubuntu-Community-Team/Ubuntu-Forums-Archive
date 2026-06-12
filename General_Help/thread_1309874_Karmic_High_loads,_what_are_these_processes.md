---
title: "Karmic: High loads, what are these processes?"
date: 2009-11-01
forum: General Help
---

### Post by Nugar on 2009-11-01
Hi all,

I'm now using Karmic, but two processes seem to be sucking my lowly CPU power.

I have gvfs-gdu-volume using 34.3% and devkit-disks-da using 22.9%

What are these? Are they necessary tu run Ubuntu? Can I just kill them?

Thanks in advance,

---

### Post by Nugar on 2009-11-02
No clues?

Cheers,

---

### Post by NightwishFan on 2009-11-02
Device kit is a new framework for handling hardware. Do you have any external drives or flash cards, or a ntfs partition?

---

### Post by Nugar on 2009-11-02
Hi NightwishFan,

Thanks for your post. yes I do have an external HDD (FAT32) and two ntfs partitions (two hard disks, actually).

---

### Post by NightwishFan on 2009-11-02
I am no expert, but through trial and error.. Perhaps try unmounting all ntfs drives and the external drive. If you need these mounted at runtime, then do not do so. If the problem stops with the external drive then it is the issue, if not then continue on with NTFS.

As I said, anything that you need mounted for Ubuntu to work do not unmount. (I dont think it will let you anyway).

If you installed via Wubi (Windows install), there is always a disk load because it is installed in ntfs, which I think is mounted through fuse.

---

### Post by Nugar on 2009-11-02
Actually it is not running right now. and the load is very low. I have a HDD formatted as ext3 with a swap area. I originally installed 9.04 there. I had previously used 8.04 and 8.10 for brief periods, but always went back to XP.

So in the end, I installed 9.04 on it own disk, but left two other disks so XP could read them.

But now, I'm almost always in Ubuntu. And when I use Windows, I use it via VMware (I haven't been able to activate my two screens with VirtualBox)

And I upgraded to 9.10 using apt-upgrade (I don't remember the exact name).

But I think I will ultimately do a clean install, since I want to see what the new GRUB is about, and see what ext4 can do for me :)

When I upgraded, it left ext3, the old GRUB, Pidgin...

---

### Post by chucknorris on 2009-11-03
Same problem here. gvfs-gdu-volume, devkit-disks-da, update-notifier and dbus-deamon consuming 10-20% CPU each. Upgraded from Jaunty to Karmic.
I have currently 1 ext3 and one ntfs partition mounted + one external disk mounted as ext3.

---

### Post by Nugar on 2009-11-03
By the way, what I did was open my System > Preferences > Startup Applications and unchecked several repeated apps, so only one runs at a time.

Also, I checked the "Automatically remember running applications when logging out" box.

And if I remember correctly I killed gvfs-gdu-volume.

The load went down considerably. Now, please test this before using the "auto remember" box, so it breaks some functionality, the daemons will run by themselves the next time you log in.

Cheers,

---

### Post by ode on 2009-11-12
I too am experiencing this problem.
I do have ntfs partitions on my drive but none of them are in my fstab.
The only partitions in my fstab are root and home (both ext4), swap and proc.

I have filed a bug at [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/481626](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/481626)

---

