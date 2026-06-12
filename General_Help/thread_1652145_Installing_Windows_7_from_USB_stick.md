---
title: "Installing Windows 7 from USB stick"
date: 2010-12-24
forum: General Help
---

### Post by Vault Dweller on 2010-12-24
Since playing games on Ubuntu is a pain, I've decided to sacrifice a few GB's to install Windows 7 on another partition. Is there any tool for Ubuntu to make USB sticks bootable? I've tried UNetbootin, but that's just for Linux distributions. I use Ubuntu 10.04 64Bit and want to install Windows Home Premium 64Bit, in case it's important...[URL="http://www.dict.cc/englisch-deutsch/sacrifice.html"]
[/URL]

---

### Post by C.S.Cameron on 2010-12-24
Format your flash drive NTFS, (gparted).
Set flash drive boot flag, (gparted).
Copy files from Windows 7 install DVD or extract iso to flash drive, (archive manager).

---

### Post by Verbeck on 2010-12-24
i recall this being posted somewhere in this forum
> 1. install gparted
2. format the flash drive as ntfs
3. copy the stuff from the cd
4. set the boot flag


---

### Post by Vault Dweller on 2010-12-24
How do I set a boot flag?

---

### Post by Verbeck on 2010-12-24
> **Vault Dweller said:**
> How do I set a boot flag?
right click the partition in gparted>manage flags>check 'boot'

---

### Post by Vault Dweller on 2010-12-24
It says "BOOTMGR is missing" so I guess I have to mount the ISO and copy the actual files on the stick, right? Which tool do you use to mount ISO files?

---

### Post by Verbeck on 2010-12-24
you could use archive mounter (from 'open with') or install gmountiso
or just extract the iso to the usb using archive manager

---

### Post by Vault Dweller on 2010-12-24
Thanks for your help, it worked. The next problem is, that Windows starts automatically. No chance to use Ubuntu (It's still on the HD). What to do?

---

### Post by MasterNetra on 2010-12-24
> **Vault Dweller said:**
> Thanks for your help, it worked. The next problem is, that Windows starts automatically. No chance to use Ubuntu (It's still on the HD). What to do?

Yea which is why you install Windows first then Ubuntu. Window's boot loader will override grub.

You can either re-install Ubuntu (the simpler yet more drastic measure), you could use Super Grub OR you can reinstall grub from live cd. For the last one see here: [http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html](http://www.ubuntu-inside.me/2009/06/howto-recover-grub2-after-windows.html)

Its from 2009 but it still works for lucid and Maverick.

---

### Post by Vault Dweller on 2010-12-24
Applause to Windows...

Thanks.

---

