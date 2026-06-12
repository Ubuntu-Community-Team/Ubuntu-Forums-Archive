---
title: "Quad boot XP Ubuntu Mint Cinnamon and Mint Mate on notebook"
date: 2012-09-14
forum: General Help
---

### Post by afz12 on 2012-09-14
I tried to install 4 OS' on my second notebook as quad-boot. Previously, dual boot went fine (XP and Mint Cinnamon) and I could make a spare partition at fat32 or ntfs. The notebook also has a SD card slot, currently using a 16 GB class 10 SD card. The SD card shows up on Mint install so I presume I can use this for swap space (e.g. 1/2 at 8 GB) and then 4 free partitions are left over on the hard drive. I tried to use these for XP (already installed), Mint Cinnamon (already installed) and made ext4 partitions for Mint Mate and then later for Ubuntu 12.04 (or 12.10 when its final release comes out later this year). However the installation complained about having multiple / for the boot option. Is there a way around this? I haven't tried just yet to use / usr or / some_other_option for the other two OS but I suspect they won't boot from these. Is this likely to occur? 

I have previously installed Linux distributions on external USB hard drives and these boot fine (bios setup has boot from USB drive option first) or I could use Virtualbox. However, although Virtualbox works well on Ubuntu it has some issues with Mint Cinnamon and Mint Mate (not supported by Oracle as yet). If I use virtualization I would need to use Ubuntu as a base OS but then I'd rather have Ubuntu 12.10 than 12.04 for this but 12.10 is only at a beta stage as yet (although Ubuntu 12.10 beta does seem stable). I'd prefer to have Mint Cinnamon as the base OS and dual boot with XP, triple boot with XP and Ubuntu 12.10 (beta - no Virtualbox versions are available for 12.10 beta) or the best option is quad-boot, adding Mint Mate to the mix. Does anyone have suggestions on how to do this, whether swap space allocated to a SD card slot will actually work, will one swap space allocation be shared between multiple OS' and how to get three / boot positions to work on a notebook? Any replies appreciated.

---

### Post by oldfred on 2012-09-14
I have many Ubuntu installs on my sdc drive. But I have XP on sda. 

How are partitions now. Post this:

sudo fdisk -lu

If you have lots of RAM (4GB or more) you may not need swap or much swap. You can share swap if you do not hibernate. Using a flash drive will be extremely slow as swap is for overflow of RAM use and hard drive is orders of magnitude slower than RAM and external flash still slower.

I use common data partitions, one NTFS for sharing with XP and another ext3 for sharing with my Ubuntu installs. Then all my installs with /home are in 25GB / (root) partitions.

---

### Post by afz12 on 2012-09-14
Thanks oldfred - excellent suggestions. I'll try these when I get back from Uni.

---

