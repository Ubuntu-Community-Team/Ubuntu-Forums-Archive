---
title: "How to reformat to NTFS?"
date: 2011-01-18
forum: General Help
---

### Post by rbailey83 on 2011-01-18
I was trying to re install windows vista, everything started ok got to the partitions wouldn't give me an option to delete and told me that partition needed to be NTFS. Only OS is ubuntu, how to i reformat the hard drive to NTFS so that i can reinstall vista and remove ubuntu?

---

### Post by WorMzy on 2011-01-18
Boot into a liveCD, open GParted, delete the Ubuntu partition and swap partition (if applicable), then reboot into the Windows installation CD.

---

### Post by rbailey83 on 2011-01-18
> **WorMzy said:**
> Boot into a liveCD, open GParted, delete the Ubuntu partition and swap partition (if applicable), then reboot into the Windows installation CD.

My dvd drive is not working, will usb work? and i just choose to boot from usb with ubuntu on it and open gparted in ubuntu? sorry good with computers with the exception of OS installations and partitions, have no idea when it comes to that stuff

---

### Post by WorMzy on 2011-01-18
Yeah, a LiveUSB stick will work in place of a LiveCD.

---

### Post by efflandt on 2011-01-18
Yes, you can use System > Administration > Startup Disk Creator to put a bootable Ubuntu iso on FAT or FAT32 USB flash (or SD in USB card reader) and boot from that if your computer is capable of booting from USB.  Sometimes even if you set the BIOS to boot USB before internal drive, you might still need to press a key during BIOS splash screen (often F12 or Esc) to select the boot device.

From that you can use System > Administration > Gparted to remove partitions on your main drive (gparted is on the iso, but not on an installed system by default, because it will not partition a drive you are running from or have mounted).  You may need to use **sudo swapoff** for any swap partition on that drive first.

---

