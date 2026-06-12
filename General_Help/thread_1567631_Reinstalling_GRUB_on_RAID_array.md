---
title: "Reinstalling GRUB on RAID array"
date: 2010-09-04
forum: General Help
---

### Post by blcArmadillo on 2010-09-04
I have a computer running Ubuntu 10.04 Desktop x64. I just bought another tb drive and wanted to combine my two drives using RAID 0. I have a MSI 890GXM-G65 motherboard and decided to use their built in RAID support. The last step of setting up RAID asked for confirmation to delete the MBR and I had a feeling things were going to go wrong but decided to chance it. Needless to say I can no longer boot into Ubuntu. I did some searching and most suggested booting into a live version of Ubuntu and reinstalling GRUB from there. I tried this but can't seem to mount the harddrives. Any ideas on how I'd go about mounting and reinstalling GRUB? Thanks in advance for any help you can offer.

---

### Post by ronparent on 2010-09-04
Look at this reference for reinstalling grub 2: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

Some further explanation. When you have your Ubuntu installed to a raid partition and are booting on the raid array, as it appears you are, the root is the raid partition you are installed to and the boot loader has to be written to the raid root drive. The installer usually tries to write the boot loader to a hard disk (sda,sdb, etc) rather than to the raid root. The nomenclature for these locations are found in /dev/mapper. After you have mounted your installed file system to /mnt as per the instructions, then the root-directory will be /mnt and the target for the boot loader will be /dev/mapper/<yourOverallRaidArrayName> as it now appears in /mnt/dev/mapper (<yourOverallRaidArrayName> will be the first so-called symbolic link preceeding the individual raid partitions). I hope this is enough to get you going. Post if you need more help.

---

