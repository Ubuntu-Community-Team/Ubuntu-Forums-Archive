---
title: "BURG Boot-Loader Error"
date: 2011-05-09
forum: General Help
---

### Post by IWantFroyo on 2011-05-09
I installed burg, following this guide: [http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/](http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/)

I am stuck at "sudo burg-install "(/dev/sda1)"'
It tells me that no such device exists.

Anyone have any suggestions?

---

### Post by wilee-nilee on 2011-05-09
> **IWantFroyo said:**
> I installed burg, following this guide: [http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/](http://www.omgubuntu.co.uk/2011/05/beautiful-burg-boot-loader-gets-ubuntu-11-04-ppa/)

I am stuck at "sudo burg-install "(/dev/sda1)"'
It tells me that no such device exists.

Anyone have any suggestions?

correct command
sudo burg-install /dev/sda 
Bootloader always goes to the mbr not the partition.
Make sure you run this when done.
sudo update-burg

Also run
sudo fdisk -l 
to confirm that sda is the HD, no numbers those are partitions just the first three letters.

---

### Post by Buntumatic on 2011-05-09
wilee-nilee probably gave a good advice, but for sake of truth, bootloader can be installed on partition, in case there is another bootloader on the MBR which will chainload it. I think some BIOS-es even allow booting from partition.

---

### Post by wilee-nilee on 2011-05-09
> **Buntumatic said:**
> wilee-nilee probably gave a good advice, but for sake of truth, bootloader can be installed on partition, in case there is another bootloader on the MBR which will chainload it. I think some BIOS-es even allow booting from partition.

Thanks.

---

### Post by Quackers on 2011-05-09
It's not a good idea though, as many file updates will then break grub.

---

### Post by IWantFroyo on 2011-05-10
Thanks for your help. Fixed this with "sudo burg-install "(hd0)"

---

