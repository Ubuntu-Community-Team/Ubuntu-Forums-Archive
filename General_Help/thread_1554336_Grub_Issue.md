---
title: "Grub Issue"
date: 2010-08-16
forum: General Help
---

### Post by Startacus on 2010-08-16
Okay, so I have a T61 with Windows 7 and Ubuntu on it and it works great. I also have a HP Mini 5102 with Windows 7 on it. I deleted the HP_RECOVERY partition and merged with my Windows partition because you can only have four partitions. I got Ubuntu Netbook Remix on a thumb drive and I installed it by telling it I want to pick between them at boot up. However, when I boot up my netbook it just goes right into Windows, no Grub. Here is what my fdisk -l looks like. 

  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          39      307200    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              39       11908    95334892+   7  HPFS/NTFS
/dev/sdb3           11908       19197    58555393    5  Extended
/dev/sdb4           19198       19457     2088450    c  W95 FAT32 (LBA)
/dev/sdb5           11908       18894    56119296   83  Linux
/dev/sdb6           18894       19197     2435072   82  Linux swap / Solaris


Any help on how I can get Grub running on this thing would be great. 

Thanks!

---

### Post by alphaamanitin on 2010-08-16
Download supergrub and use it to replace the windows MBR with grub.  
 
Hope I helped a little.

AlphaA

---

### Post by alphaamanitin on 2010-08-16
Download supergrub and use it to replace the windows MBR with grub.  
 
Hope I helped a little.

AlphaA

---

### Post by Startacus on 2010-08-16
> **alphaamanitin said:**
> Download supergrub and use it to replace the windows MBR with grub.  
 
Hope I helped a little.

AlphaA

I tried running supergrub off of my thumb drive but it just says "No DEFAULT or UI configuration directive found!"

Any suggestions?

---

### Post by alphaamanitin on 2010-08-18
Now I have nothing sorry.  I have never used supergrub off of a thumb drive.  I have also never had an error when using it.  When you installed Ubuntu did you also chose to install grub?  There should also be a way to point the Windows boot loader to boot Ubuntu, but you will have to look that up yourself as I have never done it.

AlphaA

---

### Post by Mark Phelps on 2010-08-19
Assuming you installed Ubuntu 10.04, you're dealing with GRUB2.

The link below is to the online help for GRUB2.  Look in the section dealing with Reinstalling from LiveCD:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by Startacus on 2010-08-24
> **Mark Phelps said:**
> Assuming you installed Ubuntu 10.04, you're dealing with GRUB2.

The link below is to the online help for GRUB2.  Look in the section dealing with Reinstalling from LiveCD:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

I tried to follow that but no luck. I try to install it to sdb5 which is my Linux partition and it warns that that is a bad idea so I pass it the --force tag and it installs but when I reboot it just goes straight to Windows. Is it weird that all of my hard drives are sdb as opposed to sda? Or is that just because I'm running off of the thumb drive so then the thumb drive is sda?

Any other ideas? Or is there something else I can try?

---

### Post by oldfred on 2010-08-25
You do not install grub to a partition as you have to use another boot loader to use it. You install grub to sda and if your USB flash is mounted as sda then you would install it to sdb. 

Use this to see what drive is what:

```
sudo fdisk -l
```

Then run this but you may have to use sdb:

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by Startacus on 2010-08-25
> **oldfred said:**
> You do not install grub to a partition as you have to use another boot loader to use it. You install grub to sda and if your USB flash is mounted as sda then you would install it to sdb. 

Use this to see what drive is what:

```
sudo fdisk -l
```

Then run this but you may have to use sdb:

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

That did the trick! Thanks a lot. When I was trying to install it I was typing "sudo grub-install --root-directory=/mnt /dev/sdb5" instead of just sdb. Thanks!

---

