---
title: "Dual boot problem with Ubuntu 9.04 and XP"
date: 2009-10-02
forum: General Help
---

### Post by bugabooandrew on 2009-10-02
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5)

I went to this site to try to dual-boot Ubuntu and XP. I already had Ubuntu running fine then I installed XP on the freespace. I rebooted with the Ubuntu CD and used terminal to do the first part. I typed sudo grub and then whatever commands. That did not work as i got an error 17 cannot mount this drive. I then tried it with root hd(o,4) and it seemed to work. I then edited the menu.lst to make xp hd(0,1). Big mistake. I got the OS selection menu up upon restarting but when I try to load XP i get a error 11 unrecognized device string. Do I reinstall Xp? repair the xp?

I have no idea what to do from here. In addition I don't know how to determine the hd(0, ?) (second#) that the Xp is installed on. Any help would be greatly appreciated.

---

### Post by Giblet5 on 2009-10-02
Please post the output of ```
sudo fdisk -l
``` (that's a lower case L and not a numeric 1)

---

### Post by bugabooandrew on 2009-10-03
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ed686

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         486     3903763+  82  Linux swap / Solaris
/dev/sda2             487        6565    48829567+   5  Extended
/dev/sda3            6566       60788   435546247+  83  Linux
/dev/sda4   *       60789      121600   488472390    7  HPFS/NTFS
/dev/sda5             487        6565    48829536   83  Linux

---

### Post by bugabooandrew on 2009-10-04
bump

---

### Post by Snatcher on 2009-10-04
You should of had xp installed first on your system then installed ubuntu. I have two systems that are dual boot. Had no problems running winblows and ubuntu.

---

