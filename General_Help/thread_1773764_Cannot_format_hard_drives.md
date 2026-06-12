---
title: "Cannot format hard drives"
date: 2011-06-02
forum: General Help
---

### Post by adamparr1987 on 2011-06-02
Hi all,

I am trying to install windows 7 over Ubuntu, however when i run the install disk it tells me that my hard drive is not formatted in the correct format.  I have then loaded up Ubuntu, tried to re-format using Gparted and it won't let me re-format my hard drive when I right click on it.  The only option I get when right-clicking is to unmount the drive.

Any ideas?

Thanks,

Adam

---

### Post by linuxinstalledfromhdd on 2011-06-02
Try this:

[http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/](http://www.linuxscrew.com/2010/05/06/install-windows-after-ubuntu-lucid-lynx/)

---

### Post by pricetech on 2011-06-02
You have no space for another partition.  If you format the one you're using, you'll lose Ubuntu.

Give VirtualBox a try and install your windows as a VM.

Just curious; what are you needing windows for ??

---

### Post by mick222 on 2011-06-02
The reason you cant format is your hard drive is mounted either download gparted live disk or if you have an Ubuntu live cd boot from that . You can then resize the ubuntu partition and create a partition fornmated to ntfs.

---

### Post by dnairb on 2011-06-02
> **adamparr1987 said:**
> The only option I get when right-clicking is to unmount the drive.

That's because you cannot format, relabel, move, or resize any drive partition that is mounted and being accessed by the system.

So... you need to run from a LiveCD so no drives are mounted, and format the drive.

---

### Post by whosyermonkey46563 on 2011-06-02
1 First boot on your live disk.
2 Log in as root.
3 Open gparted.
4 Make sure the volume is not mounted.
5 Make sure your swap file is also not mounted.
6 Delete root and swap partitions.
7 Format to fat 32.

---

### Post by adamparr1987 on 2011-06-02
Thanks everyone, 

@Pricetech - I'm returning to Windows because both my USB stick that I have work on and my external hard drive that has pictures, music and videos on etc would not mount on Ubuntu. I don't want to re-format either as they have lots of files on them which i wont be able to replace.

---

### Post by pricetech on 2011-06-03
So you're leaving Ubuntu and going back to Windows ??  That's cool.  Use what works for you.

In that case, you can actually boot to your Windows install disk and remove the partition with it, or use the live CD as mentioned above.

However, let your Windows install disk create and format its own partition.

---

