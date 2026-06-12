---
title: "Dual-boot ubuntu/xp, xp gives &quot;Disk Error... Press any key to reboot&quot;"
date: 2011-03-26
forum: General Help
---

### Post by buddhistmagic on 2011-03-26
I installed Ubuntu 10.10 (from USB) first to hd0,2, then installed Win XP SP3 (also from USB) to hd0,0. As nessesary I had to reinstall grub from my ubuntu live usb.

Ubuntu will boot fine however when I choose XP (from grub) it says 

```
Starting up...
Disk Error

Press any key to reboot.
```Output of **sudo fdisk -l**

```
buddhistmagic@lilpc:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2f94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7968    63998976    b  W95 FAT32
/dev/sda2            7968        8466     3999744   82  Linux swap / Solaris
/dev/sda3            8466       19458    88290304   83  Linux

```Contents of **/boot/grub/menu.lst**

```
default 0

timeout 10

title Ubuntu 10.10 (Maverick Meerkat)
root (hd0,2)
kernel /boot/vmlinuz-2.6.35-28-generic root=/dev/sda3 ro quiet splash
initrd /boot/initrd.img-2.6.35-28-generic
quiet
savedefault
boot

title Windows XP SP3
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

```Contents of** c:\boot.ini**

```
[Boot Loader] 
timeout=30 
Default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[Operating Systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /noexecute=alwaysoff 
C:\="Microsoft Windows XP Professional"
```I have also tried partition(0) in place of both partition(1) in my boot.ini.

Output of **ls /media/windows**

```
buddhistmagic@lilpc:/$ ls /media/windows
AUTOEXEC.BAT  CONFIG.SYS              NTDETECT.COM   System Volume Information
BOOT.001      Documents and Settings  ntldr          WINDOWS
boot.ini      IO.SYS                  PAGEFILE.SYS
bootsect.dos  MSDOS.SYS               Program Files

```I have tried **sudo ms-sys -2 /dev/sda1** which executed successfully but made no difference.

Any ideas on what is wrong or how to fix it?

---

### Post by linuxuser12345 on 2011-03-26
Sometimes when you split up your hard drive like that, it screws up your other operating system. Sounds like you might need to get a Windows re-installation disk

---

### Post by buddhistmagic on 2011-03-26
I don't have a disc, I use a thumb drive created by WinSetupFromUSB_0-2-2. I read I should have installed windows first and then ubuntu. I've done quite a bit of setting up in ubuntu and don't want to start over, installing windows again would put me in the same position. and I think something might be goofy about the way the thumbdrive installs it.

---

### Post by LostFarmer on 2011-03-26
Try removing from the boot.ini 
**C:\="Microsoft Windows XP Professional"  , **that is the only thing I see that not correct.

I'm not sure about this boot option.  Try removing it or do a google.
**noexecute=alwaysoff**

---

