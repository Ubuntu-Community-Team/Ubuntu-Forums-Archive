---
title: "Annoying boot text!"
date: 2010-01-24
forum: General Help
---

### Post by Mike_IronFist on 2010-01-24
I'm running Ubuntu 9.10 64-bit. My partition setup is an extended partition containing two ext4 partitions ('/' and '/home') and a 6 GB swap partition. I used Gparted on a 9.10 livecd and ran checks on both partitions, and re-formatted the swap partition. I edited /etc/fstab and /etc/initramfs-tools/conf.d/resume accordingly. However, everytime I boot, just before the GDM login screen would normally appear, instead I get a text screen that says something with "fsck linux-ng", presumably the system checking my two partitions again before mounting, and a few services are also started. Then it blinks to the GDM login.

This text is annoying! It ruins the appearance of my otherwise perfectly-smooth boot process and I need to know how to get the system to stop showing it. Any ideas?

---

### Post by dcstar on 2010-01-24
> **Mike_IronFist said:**
> I'm running Ubuntu 9.10 64-bit. My partition setup is an extended partition containing two ext4 partitions ('/' and '/home') and a 6 GB swap partition. I used Gparted on a 9.10 livecd and ran checks on both partitions, and re-formatted the swap partition. I edited /etc/fstab and /etc/initramfs-tools/conf.d/resume accordingly. However, everytime I boot, just before the GDM login screen would normally appear, instead I get a text screen that says something with "fsck linux-ng", presumably the system checking my two partitions again before mounting, and a few services are also started. Then it blinks to the GDM login.

This text is annoying! It ruins the appearance of my otherwise perfectly-smooth boot process and I need to know how to get the system to stop showing it. Any ideas?

```
sudo update-initramfs -u -k all
```

---

### Post by Mike_IronFist on 2010-01-24
> **dcstar said:**
> ```
sudo update-initramfs -u -k all
```

Thank you, it worked perfectly!

---

