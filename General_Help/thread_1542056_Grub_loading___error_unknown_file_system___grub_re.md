---
title: "Grub loading  / error unknown file system /  grub rescue"
date: 2010-07-30
forum: General Help
---

### Post by molykkutti on 2010-07-30
Hi
I 've been using a Ubuntu 10.o4 /Win XP dual booting system ...
When i booted the system i met with a rare error message 
    grub loading 
    error unknown file system
    grub rescue >

  
I booted with a live CD 

When I gave fdisk -l at the command prompt  the following was the result:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81aa81aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9729    57665287    f  W95 Ext'd (LBA)
/dev/sda5            2551        2942     3148708+   7  HPFS/NTFS
/dev/sda6            2943        5374    19530752   83  Linux
/dev/sda7            5374        5499      999424   82  Linux swap / Solaris
/dev/sda8            7651        9729    16699536    7  HPFS/NTFS


then i try  the following command 

sudo mount /dev/sda6 /mnt


I got the following as output:

mount: wrong fs type, bad option, bad superblock on /dev/sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I cant help  me any more  ..
pls anyone else .....

---

### Post by stiff01 on 2010-07-30
hello



Hi
I 've been using a Ubuntu 10.o4  but can you just give me idea about it




_________________________________
  Want   to get-on Google's first page and loads of traffic to your website? 
    Hire a SEO Specialist from Ocean Groups    [seo specialist ](http://www.oceangroups.org)

---

