---
title: "2 OS on 2 Hard Disk"
date: 2011-10-10
forum: General Help
---

### Post by ALF102 on 2011-10-10
Ok, I have one 320GB external hard disk installed with Ubuntu 11.10 and the other one is the 160GB built-in hard disk that has Windows 7 installed. What I am trying to do here is that, if I plug-in my external hard disk before I boot up my laptop, the grub menu will show up thus allowing me to choose Ubuntu to start. But the real problem occur when I don't plug-in my external hard disk and boot up from the built-in hard disk that has Windows 7, the grub crashed thus displaying "grub rescue"

My question is, is there anyway for me to remove that grub from the built-in hard disk thus allowing me to boot-up to Windows 7 without the need to plug-in my external hard disk every time I turn on the pc?

---

### Post by drs305 on 2011-10-10
You can restore the Windows bootloader with the Windows repair disks, but if the Windows files are intact you should be able to accomplish what you want from a normal Ubuntu boot (no LiveCD needed). This assumes Grub was installed on the sda MBR and not in the Windows partition. If it was mistakenly installed on the partition, you will need to repair Windows.

I will call your Windows drive sda and your Ubuntu drive sdb. [COLOR="DarkRed"]You will have to change the values in the following commands if necessary.[/COLOR]

With both drives connected, boot Ubuntu.

Install the lilo bootloader (but don't run the configuration commands):
```
sudo apt-get install lilo
sudo lilo -M /dev/sd**a** mbr

```
It will complain about configuring lilo. Do not do this.

The above commands will point the sda (Windows) MBR to the partition on the Windows drive marked as the bootable partition. If the Windows files haven't been changed, the Windows bootloader will run if BIOS boots sda.

Make sure Grub 2 is on the external MBR:
```
sudo grub-install /dev/sd**b**
```

Now make sure the BIOS is set to boot the external drive first, then the internal drive. If the external is connected, Grub will control. If it isn't, you will get the Windows bootloader.

---

### Post by ALF102 on 2011-10-10
Thanks, problem solved.

---

