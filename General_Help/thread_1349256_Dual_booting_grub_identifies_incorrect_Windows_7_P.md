---
title: "Dual booting grub identifies incorrect Windows 7 Partition"
date: 2009-12-08
forum: General Help
---

### Post by charred on 2009-12-08
Hi everyone,

Using ubuntu 9.10 64-bit, dual-booting with Windows 7 and it was working perfectly. I updated ubuntu and plugged in an extra HD now grub will not boot Windows 7, grub menu says it is /dev/sdc2 when it is /dev/sdc3, looking for a way to change it so grub thinks Windows is on /dev/sdc3. I know this because /dev/sdc2 is only 100MB in size and is a backup partition that Windows 7 creates to boot in recovery mode. 

It was working fine this morning and I have not booted Windows since then. I did update the kernel and I have plugged in another HD since I was last in Windows.

Command outputs of sudo update-grub and sudo fdisk -l outputs are here: 

```
$ sudo update-grub
[sudo] password for []: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdc5.  Check your device.map.

Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdc2
grub-probe: error: Cannot find a GRUB drive for /dev/sdc2.  Check your device.map.

done
me@mycomp:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabb35a2f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182402  1465136128    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41592eb5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   42  SFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e0958

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        6748    54203278+   5  Extended
/dev/sdc2   *        6749        6761      102400    7  HPFS/NTFS
/dev/sdc3            6761       25884   153600000    7  HPFS/NTFS
/dev/sdc4           25884      121601   768854016    7  HPFS/NTFS
/dev/sdc5               1        5714    45897642   83  Linux
/dev/sdc6            5715        6687     7815591   83  Linux
/dev/sdc7            6688        6748      489951   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Disk identifier: 0x01f21353

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           2    31008256   976760032+   7  HPFS/NTFS
```Now this mentions a problem in /boot/grub/device.map

I removed the file and then ran sudo update-grub again and the output was as follows:

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdc2
done
```

This all looks fine however as you can see it still points to /dev/sdc2, which is not Windows.

If anyone can help me I would be very grateful. Thanks.

---

### Post by charred on 2009-12-08
Alright I believe I fixed it. I'm writing this down so if anyone else has the same problem they might have something to try.

I originally thought that it was just not recognising the correct Windows partition, I do not believe this is the case. I think it doesn't like the OS drive being changed, say from /dev/sda to /dev/sdc or something. I'm certainly no grub expert.

The problem, I believe, was having the hard drive which my operating system was on to be a higher number than one I plugged in later on the motherboard. For example my OS HD was plugged into SATA_2 and a new drive was later plugged into SATA_1. This caused the drive that was originally /dev/sdb to become /dev/sdc. While I don't think this is a problem in itself, when the kernel was updated is ran the update-grub command which did something that broke it. I'm still not sure what exactly, but while the Windows partition was still there, I got a invalid error when trying to boot it. I don't know if that makes sense or is even correct at all, if it doesn't someone please enlighten me.

Okay, so grub wont let you boot Windows, and I don't know why this is but stopped me booting Ubuntu aswell.

How to fix it:

I unplugged all my HD's except for my OS drive, and put that into SATA_0 on my motherboard.

Then booted from a LiveCD and chrooted into my linux install and followed [these steps]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD").

Then restarted and notice Windows is missing from the grub menu, boot into linux normally and ran:
```
sudo update-grub
```

If you have problem in this step try making a backup of your device.map

```
sudo mv /boot/grub/device.map /boot/grub/device.map.backup
```

I believe ```
sudo update-grub
``` should generate a new one for you.

That should detect the Windows partition, reboot and confirm it works.

---

