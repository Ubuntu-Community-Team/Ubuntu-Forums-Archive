---
title: "Partitioning for windows"
date: 2009-11-03
forum: General Help
---

### Post by lynx93 on 2009-11-03
Heya!
I have ubuntu jauty on my laptop but for some programs I would need xp too. But I dont know how to start the partitioning process for it. If I just simply start to install windows there will be an option to partitionate the hard disk? Because I want to save my documents on linux. I tryed to do partition with gparted but it didnt work, there was no menu point avaible?
Please help!

---

### Post by sliketymo on 2009-11-03
> **lynx93 said:**
> Heya!
I have ubuntu jauty on my laptop but for some programs I would need xp too. But I dont know how to start the partitioning process for it. If I just simply start to install windows there will be an option to partitionate the hard disk? Because I want to save my documents on linux. I tryed to do partition with gparted but it didnt work, there was no menu point avaible?
Please help!

  Virtual machine ?

---

### Post by coffeecat on 2009-11-03
Several points:

If you just start to install Windows there is the danger that it will wipe out the whole disc and you will lose Ubuntu.

If you use a Microsoft install disc, you can point it to a pre-exisiting NTFS partition, but this **must** be a primary one, not a logical. and the installer will install the windows bootloader to the mbr, overwriting grub stage 1, so you'll have to reinstall grub if you want to boot Ubuntu.

If you don't have a Microsoft disc, but are relying on the manufacturer's restore disc, then that almost certainly will wipe the whole HD whether or not you provide a NTFS partition for it.

You might be able to shrink your Linux partition with Gparted (from the end, not the beginning), but we need more information before we can help. Post the terminal output of:

```
sudo fdisk -l
```

---

### Post by P4man on 2009-11-03
> **lynx93 said:**
> Heya!
I have ubuntu jauty on my laptop but for some programs I would need xp too. But I dont know how to start the partitioning process for it. If I just simply start to install windows there will be an option to partitionate the hard disk? Because I want to save my documents on linux. I tryed to do partition with gparted but it didnt work, there was no menu point avaible?
Please help!

Depending on the apps you need, Id also suggest using a virtual machine ( I assume you already tried win)

If you must install XP then first you must prepare your drive. Boot from a ubuntu liveCD. Run gparted and swap off you swap partition (right click it). Then you can resize and move partitions. Make empty room or a ntfs partition at the beginning of the disk (left). Thats where you will install XP on.

Keep in mind that installing windows will wipe grub, so you will have to reinstall grub from the livecd to restore a dualboot.

Also make sure to backup important stuff before starting this.

---

### Post by fbugnon on 2009-11-03
> **lynx93 said:**
> (...) I tryed to do partition with gparted but it didnt work, there was no menu point avaible?

I don't know how your HD is partitioned, but you cannot resize unless you **unmount** the partition, which means you'll probably have to use a live CD to achieve this.

Secondly, I know is not you question, but just an advice: people usually install Windows first and Ubuntu afterwards because it is easier (I should say automatically) to have GRUB auto-detect both system, as opposed to having to manually edit/restore **GRUB** after installing Windows on a computer with Ubuntu.  You might want to take a look on how this is done and evaluate if it is not easier *for you* to make a fresh install of both systems.

---

