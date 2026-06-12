---
title: "Removing drives from Places Menu in Xfce..."
date: 2009-07-19
forum: General Help
---

### Post by Avinash.Rao on 2009-07-19
Hi all,

I am using Xfce on Ubuntu Server 8,04 and I have configured 3 different Partitions for /home, /opt and /. 

I have removed this from being displayed on the desktop but the Problem is I still have an entry in the places menu for "950G Volume" that I would really like to hide. This is bcoz i have configured LTSP and all LTSP clients can see this volume.


Please help
Avinash

---

### Post by michy99 on 2009-07-19
If you set up fstab to mount it in /mnt (or anywhere besides /media) it should not show up in Places. (I think. Not 100% sure.)

---

### Post by Avinash.Rao on 2009-07-19
They are not external USB drives, they are internal hard drives configured in RAID 5 and they are mounted in /home. /opt and the root filesystem /. Don't know why they appear as Removable Drives?

---

