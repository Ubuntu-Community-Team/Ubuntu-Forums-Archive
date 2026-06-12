---
title: "Grub Error - Jaunty/WinXP Dual Boot"
date: 2009-11-03
forum: General Help
---

### Post by ColdFFF on 2009-11-03
I have an old laptop which has been running extremely slow with Windows XP. So I decided to bring it in line with the rest of my machines and install Ubuntu 9.04.

I used gparted on the livecd to resize the windows ntfs partition, leaving a boot partition at the start of the drive, and an extended partition at the end containing the root and swap partitions.

After installing however, Grub would display Error 15: File not found. I booted back into the livecd, mounted both the /boot and root partitions and took a look. The boot partition did have the kernel files, but no grub folder. No grub folder was found after a quick look over root either.

So I used sudo install-grub /dev/sda2 (correct partition for boot), which worked with no problem, rebooted and this time was presented with the Grub prompt. Back into the livecd, took a look and there was no menu.lst in the grub folder. sudo update-grub fixed this however.

Now, when attempting to boot, I receive Error 17: Cannot mount selected partition. I figured maybe it was trying the wrong partition, so I tried altering it, but this only gave me more errors, most notable Error 18 : Selected cylinder exceeds maximum supported by BIOS.

I'm assuming now that either the menu.lst, device.map or both are incorrect. Any ideas on a fix?

For reference:

Output of sudo fdisk -l
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x19061905

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *         132       15556   123901312+   7  HPFS/NTFS
/dev/sda2               1         131     1052226   83  Linux
/dev/sda3           15557       19457    31334782+   5  Extended
/dev/sda5           15557       19208    29334658+  83  Linux
/dev/sda6           19209       19457     2000061   82  Linux swap / Solaris

Partition table entries are not in disk order

```

menu.lst (trimmed to relevant section)
```
title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/home/ubuntu/aufs ro quiet splash 
quiet

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/home/ubuntu/aufs ro  single

title		Ubuntu jaunty (development branch), memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

device.map
```
(fd0)	/dev/fd0
(hd0)	/dev/sda
```


I am assuming it is most likely menu.lst is wrong, but I cant remember off hand how to correct it (been learning to use grub2). I know menu.lst doesnt currently list Windows XP at all, however this is not a concern just yet.

---

### Post by lidex on 2009-11-03
Did you install grub to the mbr? I'm having a hard time visualizing the disc layout. Here's my term output:
```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18927   152031096    7  HPFS/NTFS
/dev/sda2           18928       38913   160537545    5  Extended
/dev/sda5           18928       31085    97659103+  83  Linux
/dev/sda6           31086       37944    55094886   83  Linux
/dev/sda7           37945       38913     7783461   82  Linux swap / Solaris

```
This disk had XP installed first, then ubuntu. 

Something odd about your setup. I left windows alone other than shrinking partition. Installed ubuntu on remainder of disk in three parts -root,home,swap and installed grub to mbr. I saw something on forums today about remapping but cannot find it now. You may be better off reinstalling. Anyway some info [here]("http://ubuntuforums.org/showthread.php?p=8161184#post8161184")

---

### Post by ColdFFF on 2009-11-04
Yeah, I figured a total reinstall of everything would be the easiest option, just I'd prefer not to have to suffer installing Windows again.

---

