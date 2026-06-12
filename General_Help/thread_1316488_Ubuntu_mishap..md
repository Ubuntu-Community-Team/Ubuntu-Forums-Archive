---
title: "Ubuntu mishap."
date: 2009-11-06
forum: General Help
---

### Post by maxjax800 on 2009-11-06
I'm an Ubuntu newbie; I downloaded it upon the recommendation of PC WORLD magazine.

I had successfully installed Ubuntu 9.10 as a dual boot with Win 7.  I went to System, Administration, Hardware Drivers. Ubuntu told me to download the ATI PROPIETARY DRIVERS.  I did so, upon which I was stuck at a flashing Ubuntu login screen.

At this point, I panicked, booted into Windows 7, and using Windows 7 paritioning software, deleted the Ubuntu Partition and its swap file.

Now upon bootup, I get this error message (Grub Loading stage 1.5, Grub loading, please wait Error 22).

I do not have any Windows 7 bootable CDs. I do have the Ubuntu 9.04 CD.  Suggestions?

---

### Post by nothingspecial on 2009-11-06
Reinstall ubuntu on the now empty partition. This should fix grub and allow you to boot into windows.

---

### Post by maxjax800 on 2009-11-06
> **nothingspecial said:**
> Reinstall ubuntu on the now empty partition. This should fix grub and allow you to boot into windows.

I ran the Ubuntu 9.04 Live CD to install Ubuntu and Win 7 side by side.  However, when I drage the slider to the left, the Ubuntu partition does NOT increase in size.  There is no value in GB.  

I also see the previously deleted Ubuntu partition listed as "free space."

Am I doing this wrong?

---

### Post by nothingspecial on 2009-11-06
At the partitioning stage choose manual.

Choose to format the partition ext3 or ext4 and set the mount point as /

Don`t do anything to the windows partition and make sure you choose the right one.

---

