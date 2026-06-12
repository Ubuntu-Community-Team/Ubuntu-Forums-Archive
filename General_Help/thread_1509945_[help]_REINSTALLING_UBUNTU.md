---
title: "[help] REINSTALLING UBUNTU"
date: 2010-06-14
forum: General Help
---

### Post by splitfirex on 2010-06-14
hello everyone i got this problem, yesterday i **** up my ubuntu, and i want to reinstall it, but i have windows 7 installed in the same hd. so i want to reinstall ubuntu without touching the grub so i can access my windows partition.

---

### Post by VastOne on 2010-06-14
> **splitfirex said:**
> hello everyone i got this problem, yesterday i **** up my ubuntu, and i want to reinstall it, but i have windows 7 installed in the same hd. so i want to reinstall ubuntu without touching the grub so i can access my windows partition.

If you are trying to get back to Win7 perhaps repairing the MBR is what you need...?

Instructions [_[COLOR="DarkRed"]Here[/COLOR]_]("http://www.ehow.com/how_4836283_repair-mbr-windows.html")

If not, just install Ubuntu again and Grub will rebuild it and locate your Win 7

---

### Post by splitfirex on 2010-06-14
but how? when i try to install again ubuntu, only shows 2 options "manual <something>", and "install side by side", and i want to use my old ubuntu partition.

---

### Post by utnubuuser on 2010-06-14
at the end of the installation run through, there is an option to **not** install grub

To install on the existing ubuntu partition, select manual partitioning, then select the existing ubuntu partition, then select 'change', leave all settings as they are, ie size and filesystem type, name the partition /  that should do it. 

You might be able to get away with not installing grub, the option for that comes up under the 'advanced' tab in the last step of the installation, before the files are copied to disk, but your partitions will probably not be recognized then and you'll have to install manually afterward, which is possible and not too difficult, - I was under the impression that the installer recognizes windows 7 ok though, so I'd be inclined to let it install grub without changing any of the settings.

ps windows partitions are ntfs, and ubuntu partitions are ext3 or ext4, and if this is on a laptop, make sure you've got a swap partition of 1.5x the amount of ram in the machine (for hibernation to work properly).

If you've never done manual partitioning it can seem kinda confusing, but it isn't really.  There is an Ubuntu manual partitioning wiki too...

and have a read through this.. (though looking at it, it looks kinda confusing)> [http://ubuntuforums.org/showthread.php?t=282018]("http://ubuntuforums.org/showthread.php?t=282018")

---

### Post by splitfirex on 2010-06-14
ok thx i will try that.

---

### Post by utnubuuser on 2010-06-14
yo, here's the wiki link> [https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by splitfirex on 2010-06-15
> **utnubuuser said:**
> at the end of the installation run through, there is an option to **not** install grub

To install on the existing ubuntu partition, select manual partitioning, then select the existing ubuntu partition, then select 'change', leave all settings as they are, ie size and filesystem type, name the partition /  that should do it. 

You might be able to get away with not installing grub, the option for that comes up under the 'advanced' tab in the last step of the installation, before the files are copied to disk, but your partitions will probably not be recognized then and you'll have to install manually afterward, which is possible and not too difficult, - I was under the impression that the installer recognizes windows 7 ok though, so I'd be inclined to let it install grub without changing any of the settings.

ps windows partitions are ntfs, and ubuntu partitions are ext3 or ext4, and if this is on a laptop, make sure you've got a swap partition of 1.5x the amount of ram in the machine (for hibernation to work properly).

If you've never done manual partitioning it can seem kinda confusing, but it isn't really.  There is an Ubuntu manual partitioning wiki too...

and have a read through this.. (though looking at it, it looks kinda confusing)

WORKED, THX!!!!!!!!!!!:guitar:

---

