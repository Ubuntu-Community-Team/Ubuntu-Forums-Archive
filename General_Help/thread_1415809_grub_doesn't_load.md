---
title: "grub doesn't load"
date: 2010-02-25
forum: General Help
---

### Post by bootdoc on 2010-02-25
Tried connecting a friends windows HD to pull data from it since it got impaired by a virus and something happened to the mbr and grub would not load. My computer just hung at a blinking curser waiting for grub to load. After screwing with it for hrs I finally pointed the bios to the boot drive and instead of loading grub I was dumped to a grub prompt.  I tried booting and repairing grub from live cd and although I success message after running grub-install and update-grub it still would not load grub.  I ended up to a reinstall.  Is there a way to to repair the MBR and grub from the grub or grub-rescue prompt?  Can I make a backup of the MBR and use it to repair MBR?

---

### Post by oldfred on 2010-02-25
This has instruction on how to manually boot from the grub rescue command line:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)

Basically:
set root=(hdX,Y)
linux /boot/vmlinuz root=/dev/sdxY ro
initrd /boot/initrd
boot

You should have been able to reinstall grub from the liveCD.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

