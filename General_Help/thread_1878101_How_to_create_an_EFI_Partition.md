---
title: "How to create an EFI Partition"
date: 2011-11-09
forum: General Help
---

### Post by MaxFactor on 2011-11-09
Hi, I'm new to Linux and installed Ubuntu on my Asus Eee PC netbook. There used to be a 16MB EFI partition which contains the Boot Booster. It shaves the booting time by 5 secs or so. The partition was erased and now I need to recreate it. There used to be some instructions on a different website related that to that. All I can remember is that it is done from a Linux Terminal. As far as I can remember the EFI should have an 0xEF or something.

Unfortunately, that site no longer exists or has been down for quite some time.

I tried GParted but it doesn't give the the option to create an EFI partition, only the usual btrfs, ext2, ext3, ext4, fat16, fat32, ntfs, etc.

Can somebody give me step-by-step instructions?

Thanks.

---

### Post by tartalo on 2011-11-09
[http://ubuntuforums.org/showthread.php?t=1025920](http://ubuntuforums.org/showthread.php?t=1025920)

---

### Post by MaxFactor on 2011-11-10
> **tartalo said:**
> [http://ubuntuforums.org/showthread.php?t=1025920](http://ubuntuforums.org/showthread.php?t=1025920)
Thanks! That helped. However, for a complete dummy on Linux like myself, it took a while to figure out the error I was getting the moment I enter fdisk /dev/sda from the Terminal. I found out that even though I'm an administrator, I needed to be a root user and should type sudo -i before anything else.

---

