---
title: "restoring encrypted ubuntu 11.04 partition"
date: 2011-05-24
forum: General Help
---

### Post by kellywmosley on 2011-05-24
had a lvm (non luks i suspect) home partition on my 11.04 install.
I've since install opensue on the same laptop hoping that if i don't leave that partition alone during opensuse installation i would be able to mount and enter my key to access the data within...stupid me....
i formated my /boot and / partition, not my /home partition of 450gb.
I'm now back on ubuntu 11.04 trying to get access to my data.
i'v found the command "encryptfs-recover-private" but i only works on mounted partitons, i can't mount my encrypted partition because the system does not recongnize it. I've have to format it to mount it.

fdisk
(bold is my encrypted partition)
   
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13       96256   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60679   487303169    f  W95 Ext'd (LBA)
/dev/sda4           60679       60802      984064   82  Linux swap / Solaris
/dev/sda5              13        2624    20978688   83  Linux
**/dev/sda6            2625       60679   466323456   83  Linux**


sudo cryptsetup luksOpen /dev/sda6 crypt1 
returns 
Device /dev/sda6 is not a valid LUKS device.

Am i buggered????
no backup before you ask...

cheers
kelly

---

### Post by mk4umha on 2011-06-25
I got this same problem, i have a raid partition that is dmcrypted that won't unlock during boot (cryptsetup: evms_activate not available" nor will it unlock under the live boot. Anyone know how to fix this on 11.04?

---

