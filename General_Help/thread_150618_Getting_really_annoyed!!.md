---
title: "Getting really annoyed!!"
date: 2006-03-26
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2006-03-26
Linux won't mount my sony psp anymore. I NEED to fix this problem, but i don't know how. If i can't ix it, i guess it'll be windows for me, i mean, whats the point of having a PSP if you can't hook it up to your PC?

When i connect it, it dosen't pop up like usual. I open nautilus and click Computer ,on the top. I click on Sony PSP and it says:

Unable to mount the selected volume. The volume is probably in a format that cannot be mounted.

I clicked on more details and this is what it said:

mount: wrong fs type, bad option, bad superblock on /dev/sda,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

mount: wrong fs type, bad option, bad superblock on /dev/sda,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Error: could not execute pmount


I've been using it for months, without problems. No matter what I try I can't fix the problem. I've tried booting up with it in USB mode and changing USB plugs, but nothing works.

I'm desperate!!!

NEED HELP!!!

---

### Post by Ramses de Norre on 2006-03-26
You don't need to start 3 threads for one problem, that can get pretty annoying too..
Is your psp included in the output of sudo fdisk -l when it's connected? What filesystem is it normally?

---

### Post by s_h_a_d_o_w_s on 2006-03-26
when I type sudo fdisk -l this is what I get:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7394    59392273+  83  Linux
/dev/hda2            7395        7476      658665    5  Extended
/dev/hda5            7395        7476      658633+  82  Linux swap / Solaris

Disk /dev/sda: 489 MB, 489160704 bytes
32 heads, 32 sectors/track, 933 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         932      476683+   6  FAT16


I'm pretty sure that sda1 (the last one, right on top of this message) is my PSP.

P.S. Sorry for posting those threads, it's just that no one was replying and this is a really big problem for me.

---

### Post by aysiu on 2006-03-26
```
sudo umount /dev/sda1
sudo mkdir /psp
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` add this line ```
/dev/sda1 /psp vfat iocharset=utf8,umask=000 0 0
``` Save and ```
sudo mount -a
```

---

### Post by s_h_a_d_o_w_s on 2006-03-26
I tried all of that and when i type sudo mount -a, nothing happens

---

### Post by aysiu on 2006-03-26
[QUOTE=s_h_a_d_o_w_s]I tried all of that and when i type sudo mount -a, nothing happens[/QUOTE] What do you mean by "nothing"? Certainly nothing *visibly* happens, but if you go to the /psp folder, your PSP should be mounted there.

---

### Post by s_h_a_d_o_w_s on 2006-03-26
i'm so dumb, Thanks alot aysiu, It worked!!!

---

### Post by aysiu on 2006-03-26
[QUOTE=s_h_a_d_o_w_s]i'm so dumb, Thanks alot aysiu, It worked!!![/QUOTE] Awesome! Had me worried there for a second...

---

