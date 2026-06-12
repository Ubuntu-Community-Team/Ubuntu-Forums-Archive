---
title: "Can't turn on encrypted swap after I've turned it off."
date: 2009-07-27
forum: General Help
---

### Post by voyagi on 2009-07-27
I have three encrypted partitions on my laptop (the standard encryption in the ubuntu alternate-installation cd), root, /home and swap, and of course an unencrypted /boot. I got tired of having to write all three passwords every time I booted my computer, so I turned my swap off using "swapoff" and removed the swap-line in fstab since I have 2 gb ram and never use more than 500 mb of it. But still I had to type the password to the swap. What I didn't realise was that without a swap you can't hibernate. When I add the swap-line in fstab my swap is still not used, and "swapon -a" gives no output. When I try "swapon -a /dev/mapper/sda3_crypt" it's busy.

My fstab:
```
proc            /proc           proc    defaults        0       0
/dev/mapper/sda2_crypt /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=3e518fab-671b-4d72-9434-d395cbbe7a11 /boot           ext3    relatime        0       2
/dev/mapper/sda4_crypt /home           ext3    defaults        0       2
/dev/mapper/sda3_crypt 	swap 		swap 	defaults 	0 	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

