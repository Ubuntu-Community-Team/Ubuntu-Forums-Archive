---
title: "Reinstalling mbr (vista)"
date: 2011-03-21
forum: General Help
---

### Post by sports fan Matt on 2011-03-21
Since I'm having a friend help me fix my Ubuntu partitions by reinstalling my ubuntu partitions, I need help accessing my vista partition on SDA1 so I can at least get back to it until he has time to help me fix grub in ubuntu.  

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00070abe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   299025214   149511583+   7  HPFS/NTFS
/dev/sda2       299026430   976773119   338873345    5  Extended
/dev/sda5       520914944   964749311   221917184   83  Linux
/dev/sda6       964751360   976773119     6010880   82  Linux swap / Solaris


How can I get back SDA1 so I can get back booting into vista while waiting for a repair of Ubuntu's grub?

---

### Post by Neojack14 on 2011-03-21
Simply run this disc via USB or cd
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

Run GAG then select uninstall. It will remove any boot menu and put back the mbr. You don't need to install gag to uninstall it.

This is what I used to remove grub and other boot menus.

Hope this Helps:P

Neojack14

---

### Post by sports fan Matt on 2011-03-21
I fixed my ubuntu partition, but cant boot into vista and I don't have a cd to burn..can anyone help?

---

### Post by sports fan Matt on 2011-03-21
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   299025214   149511583+   7  HPFS/NTFS
/dev/sda2       299026430   976773119   338873345    5  Extended
/dev/sda5       520914944   964749311   221917184   83  Linux
/dev/sda6       964751360   976773119     6010880   82  Linux swap / Solaris

---

