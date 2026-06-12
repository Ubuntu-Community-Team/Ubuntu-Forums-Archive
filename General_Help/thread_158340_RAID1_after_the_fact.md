---
title: "RAID1 after the fact?"
date: 2006-04-11
forum: General Help
---

### Post by phrophrosty on 2006-04-11
Hey,

I have a server set up. It has 2 hard drives in it. One disk is being used as swap and / . The other hard drive is the same size, make, model, but is empty. 

Is there any way i can get this to be RAID1 without starting from scratch. As in, keep the current install.

Thanks

---

### Post by lcg on 2006-04-11
[QUOTE=phrophrosty]I have a server set up. It has 2 hard drives in it. One disk is being used as swap and / . The other hard drive is the same size, make, model, but is empty. 

Is there any way i can get this to be RAID1 without starting from scratch. As in, keep the current install.[/QUOTE]
Yes, there is, but it is ugly. I'll give you a rough list of what to do, if you need more, just ask. A warning, though: **The following is a dangerous procedure and it can go wrong. Make a backup before you start if you're working with important data!**

[LIST=1]
[*]Create a second / and swap on the second drive, the same size as on the first drive. Let's assume / is /dev/hdc1, swap /dev/hdb2.
[*]Install mdadm ('apt-get install mdadm')
[*]**Boot from a live CD.**
[*]Modprobe 'raid1'.
[*]Use 'mdadm -C /dev/md0 -l raid1 -n 2 /dev/hdc1 missing' to create a so called degraded array, meaning that half of the raid1 is initially missing.
[*]'mkfs' on /dev/md0 (ext3, reiserfs, ...).
[*]Mount the old / to /mnt/old, /dev/md0 to /mnt/raid (create the directories first).
[*]'cd /mnt/old'
[*]'cp -a * /mnt/raid'
[*]'cd /mnt/raid' and 'umount /mnt/old'
[*]'mdadm -a /dev/md0 /dev/hda1' will add /dev/hda1 to your previously degraded array, rebuilding the raid.
[*]'watch cat /proc/mdstat' to see the progress of the rebuild.
[*]After rebuilding is complete, edit /mnt/raid/etc/fstab and change the location of / to /dev/md0.
[*]While you're at it, add your second swap. The kernel will automatically load balance between these two swaps (unless you give them different priorities).
[*]Unmount all your partitions, reboot and remove the live CD, Ubuntu should now start from your shiny new raid1.
[*]Enjoy or restore your backup if something went wrong (you've made one, haven't you?).
[/LIST]

HTH,
Lars

---

### Post by lha on 2006-04-11
See /usr/share/doc/mdadm/rootraiddoc.97.html. It's part of package mdadm, so you should have it already on your computer. It assumes you want to use lilo, but you can use grub, too, if you want.

---

### Post by phrophrosty on 2006-04-13
LCG,

Thanks for the help. I dont know if i will be able to do the conversion as its in a production machine. But if i try it out i will let you know how i go.

---

