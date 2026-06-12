---
title: "Lost /home directory pls help"
date: 2010-05-23
forum: General Help
---

### Post by ashwinrao on 2010-05-23
I had a different /home directory and /swap for my Ubuntu installation. I used dual boot with XP. I have tried to install another distro along with it. I made /home and /swap common for both. After installation, I have left with free space hence I went to XP Administrative tools tools to format it. (I really feel sad I used Windows to do that) In the process, I lost my /home directory automatically and other partitions also displayed as 'unallocated'. I'm not feared for the data loose since I am having the backup of other partitions. My concern now is my both Ubuntu and Kubuntu installations display message as unable to mount /home directory and doesn't logs me in. However, XP works fine. Please show me the way to restore my Ubuntu and Kubuntu installations. I can do fresh installation but my Internet connection is slow and it takes me lot of time to restore my Ubuntu installation. Is there any way so that I can create /home directory for both the distros?

---

### Post by ashwinrao on 2010-05-23
Bump!:confused:

---

### Post by SlidingHorn on 2010-05-23
Please wait before bumping a thread.  It's normally recommended to give it about 24 hours.  Lots of questions to answer on the forums, and it's not exactly prime time right now.

Someone will come along as soon as they can.  Hang in there! :)

---

### Post by spiky001 on 2010-05-23
Hi I have triple booted with open suse, I was told not to have the same home folder, but not sure with both being ubuntu based tho nut itmight be wworth setting 2 homes. I used 1 swap for both distros tho

---

### Post by Jakiejake on 2010-05-23
> **ashwinrao said:**
> Bump!:confused:

Whoa Whoa Whoa 8mins then BUMP! LOL a bit to fast there

---

### Post by ashwinrao on 2010-05-23
Sorry for that! I was impatient and feared that my post will be stagnated and will remain unnoticed by any. Lol! I got attention of many now!:P

---

### Post by spiky001 on 2010-05-23
Just a thought if you use the boot with the live cd use gparted make sure Home is mounted

---

### Post by ashwinrao on 2010-05-23
I have checked this method. There is no other partitions are visible except my xp, Ubuntu, Kubuntu and one unallocated partition. It is the fault of XP Disk Management tool which deleted the other 2 partition along with my /home while correcting the unused space of my disk. However, I got [this]("http://ubuntuforums.org/archive/index.php/t-1055924.html") in Google and I'm posting the outcome here when I get home.

---

### Post by ashwinrao on 2010-05-23
Studied the above mentioned link but unable to understand it. The output of sudo fdisk -l is: Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x248a2489

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1913    15366141    c  W95 FAT32 (LBA)
/dev/sda2            1914       16048   113539357    f  W95 Ext'd (LBA)
/dev/sda3           16049       19452    27342630   83  Linux
/dev/sda5            1914        3209    10406250   83  Linux
/dev/sda6            3210        5626    19414521    7  HPFS/NTFS
/dev/sda7            5627        8707    24748101    7  HPFS/NTFS
/dev/sda8   *        8708       14213    44226913+  83  Linux
/dev/sda9           14214       16048    14739606   82  Linux swap / Solaris

Can any body give right direction and the steps please?

---

### Post by ashwinrao on 2010-05-24
Lost the battle :(. The details above provided are after creating /home and /swap manually. But I was unable to log into the Ubuntu installation. Solved the issue by doing  the clean installation again for Ubuntu.

---

### Post by Jakiejake on 2010-05-24
> **ashwinrao said:**
> Sorry for that! I was impatient and feared that my post will be stagnated and will remain unnoticed by any. Lol! I got attention of many now!:P

LOL
Thats Okay :popcorn:

---

