---
title: "Remove xp from dual boot with ubuntu"
date: 2010-01-27
forum: General Help
---

### Post by Juand_au on 2010-01-27
Hi,

I have a 20gb partition for xp and 140gb for ubuntu, i dont want the xp partition anymore as i found out about virtual box and i rather use it that way when i need to use photoshop which is the only thing that keeps me from deleting xp. I already have my ubuntu configured the way i want it and i dont want to reinstall everything again, i just want to delete the xp partition and give that space to the ubuntu partition and then use xp with virtual box whenever i need to use photoshop. Please could anyone help me achieve this, is it possible. Thanks for your help.

Cheers 
Juan

---

### Post by ajgreeny on 2010-01-27
Very possible, and also very easy.

For safety's sake backup first.  Now boot to the ubuntu live CD or install and run gparted from System ->Administration menu (Partition Editor in 9.04).  Using that you can simply delete the WinXP partition, and if you want, using the live CD, you can move the ubuntu partition to the front of the drive, using the Resize/Move icon in the taskbar.  This taskes a long time, so you may prefer to keep that space separate as a new ext3 or ext4 partition for use in ubuntu.  It can easily be automounted with fstab edits, and labeled as Data, or Music, for example, with gparted.

If you are using karmic, a simple ```
sudo update grub
``` after the windows deletion will work to edit the grub menu, if using jaunty or earlier you will need to edit the windows entry out manually with ```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Leppie on 2010-01-27
> **ajgreeny said:**
> ... so you may prefer to keep that space separate as a new ext3 or ext4 partition for use in ubuntu.  It can easily be automounted with fstab edits, and labeled as Data, or Music, for example, with gparted.
i would go for this option, it's the easiest. just mount the newly created partition where you want.

> **ajgreeny said:**
> If you are using karmic, a simple ```
sudo update[COLOR=Red]**-**[/COLOR]grub
``` after the windows deletion will work to edit the grub menu
you forgot the hyphen between update and grub.

---

### Post by Juand_au on 2010-01-27
thanks so much, that worked perfect, i went for the resizing option, it did take a lot of time like you said, took like 2 hours but everyting is working perfect.


Cheers

---

