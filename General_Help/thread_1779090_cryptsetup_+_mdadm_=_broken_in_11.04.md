---
title: "cryptsetup + mdadm = broken in 11.04"
date: 2011-06-09
forum: General Help
---

### Post by Xebec on 2011-06-09
**Old days (long story):** One and a half years ago I had 9.10 and 4 brand new hard drives to build an mdadm based RAID5 array. To make the array protected, I decided to encrypt the drives with LUKS. At first I tried creating RAID5 and then creating an encrypted partition with cryptsetup on top of it. The problem was that kcryptd was (don't know how it is right now) single threaded - which greatly slowed my RAID5 from 260 MBps down to about 90 MBps at raw reads. So I decided that I'm smarter than that and reverted the setup: I encrypted every drive first, and then built RAID5 from the resulting /dev/mapper/* devices. Key files were used to decrypt every single drive (except my root partition drive, which was password protected) in /etc/crypttab. The boot process was smooth, and everything mounted automatically. 4 kcryptd processes were running on my Quad core CPU, making my new raw reads go up to 160 MBps!

**Fast forward to today:** Since 9.10 went out of support two months ago, I decided to renew the OS to 11.04. mdadm simply fails to notice my /dev/mapper devices during boot process and does not mount the array, but happily assembles it after I type 'madadm --assemble /dev/md0' in console. All: /etc/crypttab, /etc/mdadm/mdadm.conf, and /etc/fstab - are configured to explicitly decrypt, assemble and mount the array - the way I configured them in 9.10. But mdadm does not work now, even when I put 'mdadm --assemble /dev/md0'  in crontab with @reboot :(

Could anybody tell me how to properly fix this problem, and make mdadm discover and assemble my array? I understand I can put it into .bashrc, but this is not a good solution.

---

### Post by Xebec on 2011-06-10
Had an unexpectedly simple but not very pretty resolution by removing my config in mdadm.conf. This obviously killed my ability to assemble /dev/md0 without --scan, but also apparently gave a green light for mdadm/UDEV incremental autoassembly during boot. Strangely one of my disks got out of sync, and now mdadm is recovering it. :|

---

