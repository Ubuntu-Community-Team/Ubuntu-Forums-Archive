---
title: "Grub takes too much time to load!"
date: 2009-12-01
forum: General Help
---

### Post by LightThunder on 2009-12-01
Hello!I just Installed Ubuntu :D :D
Problem is:
After the BIOS it says 
IDE-0 found...OK
Loading Grub.

Partitions are in ext4.

It loads but, from that to the screen of the options it takes 38 seconds!

---

### Post by namok on 2009-12-01
If you have more than one disk, it may be helpful [http://ubuntuforums.org/showthread.php?p=8234882](http://ubuntuforums.org/showthread.php?p=8234882)

---

### Post by oldfred on 2009-12-01
I have Karmic on my sdc drive and was booting slowly from my sda drive.

I installed grub2 to the mbr of sdc and in BIOS set that drive to boot first and now the boot is a lot faster, but not instantaneous.

---

### Post by namok on 2009-12-01
> **oldfred said:**
> I have Karmic on my sdc drive and was booting slowly from my sda drive.

I installed grub2 to the mbr of sdc and in BIOS set that drive to boot first and now the boot is a lot faster, but not instantaneous.
Do you have done this:```
sudo dpkg-reconfigure grub-pc
```[IMG]http://www.google.pl/images/cleardot.gif[/IMG]

---

### Post by oldfred on 2009-12-01
I do not remember but I think so. I was somewhat surprised that reordering drives in BIOS did not change anything else. sda, sdb, & sdc are all the same. device.map was still that same also.

---

