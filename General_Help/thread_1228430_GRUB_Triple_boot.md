---
title: "GRUB Triple boot"
date: 2009-07-31
forum: General Help
---

### Post by DanSchnell on 2009-07-31
I'm trying to triple boot with Ubuntu, XP and Win 7 but am having some issues.  I removed the Windows boot loader already, but when i try to boot windows 7 from GRUB it boots Windows XP.  When i try to boot Windows XP, it actually loads XP.  Is there something wrong with my menu.lst?

```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		0bbd4062-a6be-499c-a3b5-9ecbf2539977
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0bbd4062-a6be-499c-a3b5-9ecbf2539977 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		0bbd4062-a6be-499c-a3b5-9ecbf2539977
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=0bbd4062-a6be-499c-a3b5-9ecbf2539977 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		0bbd4062-a6be-499c-a3b5-9ecbf2539977
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader +1

title		Windows 7
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader +1
```

Also, can you use UUID when try to boot Windows?

Here's my UUID list.

```
/dev/sda1: UUID="D61CC7981CC77253" LABEL="Windows XP" TYPE="ntfs" 
/dev/sdb1: UUID="6D5A3C901F23FE38" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb5: UUID="0bbd4062-a6be-499c-a3b5-9ecbf2539977" TYPE="ext3" 
/dev/sdb6: TYPE="swap" UUID="7c62aeba-2f8f-44f1-a407-9e83af72fe24" 

```

Any help would be great...

---

### Post by DanSchnell on 2009-07-31
bump :(

---

### Post by hibliss on 2009-07-31
lease post results of

```
sudo fdisk -l
```

From what you have posted, it looks right.

---

### Post by louieb on 2009-07-31
Do you get the option to boot win7 after you boot XP. Dual booting two MS products is kinda weird. When you install the 2nd one  it puts it boot loader in the 1st.  You should be able to boot either of your win install from there

As you can see even thought GRUB chainloading different partitions they the code windows put in the partition boot record (aka VBR) (every partition has a VBR) and does much the same thing as an MBR -  points to the same windows install of NTLDR.

---

### Post by DanSchnell on 2009-07-31
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x279a279a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30393   244131741    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75a575a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10652    85562158+   7  HPFS/NTFS
/dev/sdb2           10655       14593    31640017+   5  Extended
/dev/sdb5           10655       14425    30290526   83  Linux
/dev/sdb6           14426       14593     1349428+  82  Linux swap / Solari
```

I don't remember it giving an option for Win7

---

### Post by ppirilla on 2009-08-01
GRUB is configured correctly, this is entirely a Windows isue.

When you installed the second windows system, it automatically configured your computer to dual-boot between the two, with XP as the default option.  I'm not 100% on how to switch between the two, but I think you need to press F8 immediately after GRUB triggers the windows loader to bring up the boot menu.

---

### Post by hibliss on 2009-08-01
Boot into Windows XP and go to Start>Run> type msconfig. Go to boot.ini tab.

Look for a Windows 7 option there. Strange really that it is suddenly defaulting to XP, because Windows 7 uses the new bootloader, and should have overwritten boot.ini, unless you installed 7 first, then XP?

---

### Post by DanSchnell on 2009-08-01
I used easyBCD to remove the Vista (Windows 7) bootloader.  I've tried using EasyBCD to add Linux to the Entry list and using its NeoGrub, but haven't had any success getting back into Ubuntu. (Neogrub ends up giving me error 17 missing kernel when its still there and the entry list just doesn't work)

After booting into windows, my boot.ini shows as follows:

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\Windows="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT

```

No mention of Win 7.

---

### Post by DanSchnell on 2009-08-01
bump again...

---

### Post by hibliss on 2009-08-01
> **DanSchnell said:**
> I used easyBCD to remove the Vista (Windows 7) bootloader.  I've tried using EasyBCD to add Linux to the Entry list and using its NeoGrub, but haven't had any success getting back into Ubuntu. (Neogrub ends up giving me error 17 missing kernel when its still there and the entry list just doesn't work)


This was where you went wrong. NTLDR (Windows XP's bootloader) cannot handle Windows 7. You have to use the new BCD bootloader and allow it to handle XP and Win 7.

Here is what you need to do. First with the Windows 7 disc, you need to boot the Windows 7 install DVD, and choose "Repair" and "Command Prompt". At the prompt, do a "bootrec /RebuildBCD" to write down a new bootloader.

After this, BCD will overwrite Grub and NTLDR. Next you will need to make sure that when you boot up, that BCD recognizes the  Win XP partition, and allows you to boot in to both. If it does not, you will need to use easyBCD again, but this time you will be using it to add the option to the menu to boot XP.

After this, you will need to boot with your Ubuntu LiveCD to restore Grub. There is a thread here that discusses this -- [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

After restoring GRUB, you may need to edit the boot entries to add the Chainloader for the BCD Bootloader. You will really only need one option in the GRUB menu for Windows, which will take you to the BCD bootloader where you will be able to choose XP or Win 7.

I know this seems like a lot of work. You may be able to restore BCD using easyBCD from within Win 7, but I do not have experience with that, so google may help you there.

---

### Post by DanSchnell on 2009-08-01
Thanks for the help, but i'm really looking to get all my options on one boot screen, and not having to keep going through a bunch of boot loaders...  I haven't had any good luck getting EasyBCD to get me back into Ubuntu

---

### Post by hibliss on 2009-08-01
> **DanSchnell said:**
> Thanks for the help, but i'm really looking to get all my options on one boot screen, and not having to keep going through a bunch of boot loaders...  I haven't had any good luck getting EasyBCD to get me back into Ubuntu

This won't happen with the triple boot setup you have as far as I know. Windows 7 using a different bootloader than XP, and that combined with GRUB needing to be written to the master boot record make it very difficult.

There are some haves to get NTLDR to boot Linux (and I would not trust them), but none yet for BCD.

You are really stuck with this option. This is an old thread, but still applies to your issue, because Vista and 7 use the same bootloader - [http://ubuntuforums.org/showthread.php?t=220452]("http://ubuntuforums.org/showthread.php?t=220452")

My advice is probably the best you will get, but it does involve two bootloaders. Good luck trying to get them all to boot directly from one.

---

### Post by DanSchnell on 2009-08-01
One more issue then.  I tried to paste my menu.lst into EasyBCDs NeoGRUB (whose option shows up on the Win 7 Loader), and it DOES actually send me to the GRUB screen, but i select Ubuntu and the correct kernel it gives me Error 17 in reference to kernel:

```

 Kernel /boot/vmlinuz-2.6.28-14-generic root=UUIDf9a34018-88e1-4ddd-bc1e-24bbf280d7a6 ro quiet splash.
Error 17: File not found.
```

Edit: The UUID has changed since then, but my point is still relevant

---

### Post by louieb on 2009-08-01
The UUID on the kernel line tell  the kernel where the root file-system is 
 The line you need to fix is the root line just above the kernel line. This tells GRUB which partition /boot/vmlinuz-2.6.28-14-generic is on.

Don't know if NeoGRUB  understands **uuid** you may have to use something like 
```
root  (hd1,4) 
```where (hd1,4) is the partition in GRUB speak  that hold the kernel.

---

