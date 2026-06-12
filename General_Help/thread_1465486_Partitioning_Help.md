---
title: "Partitioning Help"
date: 2010-04-29
forum: General Help
---

### Post by ALF102 on 2010-04-29
Hi, I want to install Linux Ubuntu Netbook Remix on my Fujitsu M2010. I proceed the installation by using the Ubuntu Live USB and the problem occur when I arrive at the partitionning step. Usually there are suppose to be 3 choices which is:
      1-Install them side by side
      2-Erase and use entire disk
      3-Specify partitions manually
but when I arrive at that point there's only 2 choice which is erase and use entire disk and specify partitions manually. So since I can't install ubuntu automatically, I choose to manually specify the partitons which I haven't done before and that's why I'm asking for your help. What exactly must I specifically specify?

---

### Post by Mark Phelps on 2010-04-29
If you have an existing OS installed on that box, and Ubuntu isn't seeing it, then either of the other options is going to wipe out what you have -- which is OK if that is what you want to do.

If you want to dual-boot with an existing OS, then don't attempt to do it from the Ubuntu installer because, if you have Win7 on your box, you run a risk of corrupting the OS partition in the process.  In that case, better to launch the Win7 Disk Management utility, shrink the OS, reboot into it to confirm it works, and then use Manual Partitioning in the Ubuntu installer.

---

### Post by ALF102 on 2010-04-29
Forgot to mention that I'm using Win XP.

---

### Post by ubun_two on 2010-04-29
The general steps are:

1, Shrink the XP partition.  Make sure that XP partition is the left-most partition (Windows doesn't seem to like being on a secondary partition).  I am not sure if what Mark says is true about danger of shrinking the OS using manual partitioning.  Maybe it's better safe than sorry.

2, On the free partition, you'll need a root partition (/).  Swap partition is optional but recommended.  You could choose to add /home partition as well, which is very typical.

---

### Post by bodhi.zazen on 2010-04-29
Sounds as if you are going to want to manually specify partitions.

To do this I suggest you first run gparted and make the target partitions (resize windows -> apply changes -> make a root and swap partition for Ubuntu -> apply changes), then run the installer and specify the partitions ...

---

