---
title: "Dual boot after install?"
date: 2011-03-29
forum: General Help
---

### Post by kkelly77 on 2011-03-29
I am looking into dual booting my laptop, currently running Ubuntu 10.04, with Windoze XP.

I've searched for some "how to's" but all I'm finding are guides that explain how to setup dual booting with fresh installs of both OS. 

I've had Ubuntu running on my laptop for the past year so don't want to reinstall. I tried GParted but it does not allow me to alter the size of the partition on my hard drive. Can anyone shed some light? Thanks.

K

---

### Post by nice_like_rice on 2011-03-29
You can't change the size of a partition thats mounted, so boot Ubuntu off a live cd and then use GParted from there to make a new partition, and format it to ntfs.

Install windows on the new partition.

Windows will overwrite your MBR so you only boot into windows.

You must then put the live cd in again, and reinstall grub. There are tutorials around on how to do this.

Hope this helps!

---

### Post by kkelly77 on 2011-03-29
Thanks nice_like_rice

---

