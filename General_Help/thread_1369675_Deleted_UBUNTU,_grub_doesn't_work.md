---
title: "Deleted UBUNTU, grub doesn't work"
date: 2010-01-01
forum: General Help
---

### Post by aatami on 2010-01-01
Hello everyone,

Recently I installed Ubuntu, but since the windows programs where too slow through wine, I deleted the partition(s) that  I had installed Ubuntu on.

Now when I boot my computer, it just says "unknown filesystem" and then "grub rescue>"

I have already googled for several hours, but haven't found any help yet.

I tried the windows CD trick (Pressing R etc...), but I get the "blue screen" and I am thus forced to shut down my computer.

I have Windows XP Pro on my computer (and it's CD), and have a live CD for Ubuntu 9.10.

---

### Post by Leppie on 2010-01-01
boot with the ubuntu livecd, open a terminal and issue these commands:
```
$sudo apt-get install lilo
$sudo lilo -M /dev/sda mbr
```

---

### Post by -kg- on 2010-01-01
[LIST]
[/LIST]

Yep, when you deleted your Ubuntu partition, you deleted GRUB Stage 2, 3, and likely 1.5 along with it.  Only Grub Stage 1 (and in certain circumstances, Stage 1.5) are included in the MBR (Master Boot Record).  The rest of GRUB is contained in your /boot partition which, unless you created a separate /boot partition, is contained in your / (root) partition.

lilo will work, but you should be able to [reinstall XP's bootloader]("http://www.neowin.net/forum/lofiversion/index.php/t292614.html"), which is described at the link, as long as you're able to boot to your XP installation disk.  Read down the list of posts.

---

