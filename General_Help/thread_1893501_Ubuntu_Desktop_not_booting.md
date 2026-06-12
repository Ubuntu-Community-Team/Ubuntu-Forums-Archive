---
title: "Ubuntu Desktop not booting"
date: 2011-12-10
forum: General Help
---

### Post by arnefm on 2011-12-10
My computer has been working fine since the release of 11.10. Today it suddenly will not boot. I get to the grub menu and select the default entry. The I see the usual error (error: sparse file not allowed). This is normal, as I am using btrfs for /boot. 
Then the screen goes blank (monitor says "No video signal").
Booting into safe mode works, except that the option "netroot" does not give any network access. 

I used boot-repair and made this boot info script: [http://paste.ubuntu.com/765970/](http://paste.ubuntu.com/765970/)

---

### Post by BC59 on 2011-12-10
I think it's a problem of BTRFS. The story of this file system is very sad. It started like a winner but we are in the same point almost 2 years now. I don't recommend you to use it. It's fast but when you are caught in a problem, there is no way out. Everything is lost.

---

### Post by arnefm on 2011-12-10
Thank you for your answer.

As I said, booting into recovery mode works as it should. I have checked the filesystem on all partitions and found no problems. However I noticed an error during reinstallation of the kernel, right after update-initramfs.

W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-2.fw for module r8169
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8168f-1.fw for module r8169

---

### Post by BC59 on 2011-12-10
In that case look here:

[http://www.davidgis.fr/blog/index.php?2011/05/06/800--resolu-solved-w-possible-missing-firmware-lib-firmware-rtl_nic-rtl8105e-1fw-for-module-r8169](http://www.davidgis.fr/blog/index.php?2011/05/06/800--resolu-solved-w-possible-missing-firmware-lib-firmware-rtl_nic-rtl8105e-1fw-for-module-r8169)

---

