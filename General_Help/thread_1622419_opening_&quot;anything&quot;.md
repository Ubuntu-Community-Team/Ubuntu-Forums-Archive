---
title: "opening &quot;anything&quot;"
date: 2010-11-15
forum: General Help
---

### Post by ByteOneZero on 2010-11-15
befuddled user here.had no trouble till i needed it.gparted won't open to give access to my drives.had no issue till i needed to use it.p.s. ican't seem to grasp the concept of using the terminal command line,because every time i type OR paste the program wont run or install whichever i am trying to accomplish .i'll be patient since i've been trying to make ubuntu work for 6 wks now.help anyone??

---

### Post by TeoBigusGeekus on 2010-11-15
What message does
```
gksu gparted 
```
give?

---

### Post by Enigmapond on 2010-11-15
Not clear on what you are looking to do. To open gparted in the terminal you will need to preface it with gksu or sudo and give your password...the same holds true for installing.. example:

```
gksu gparted
``````
sudo apt-get install package name
```

---

### Post by ByteOneZero on 2010-11-15
-desktop:~$ gksu gparted
======================
libparted : 2.2
======================
Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0xd40f0a]
  15: /lib/libparted.so.0(+0x42507) [0xd78507]
  14: /lib/libparted.so.0(+0x43317) [0xd79317]
  13: /lib/libparted.so.0(+0x4460c) [0xd7a60c]
  12: /lib/libparted.so.0(+0xf7b1) [0xd457b1]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0xd49032]
  10: /lib/libparted.so.0(+0x45fa3) [0xd7bfa3]
  9: /lib/libparted.so.0(+0x4619f) [0xd7c19f]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0xd49e15]
  7: /usr/sbin/gpartedbin() [0x80901e6]
  6: /usr/sbin/gpartedbin() [0x809fc9b]
  5: /usr/sbin/gpartedbin() [0x80c0532]
  4: /usr/lib/libglibmm-2.4.so.1(+0x30eb2) [0x184eb2]
  3: /lib/libglib-2.0.so.0(+0x65def) [0x2d6def]
  2: /lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0xe9696e]
  1: /lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0x107ea4e]
Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:659 in function probe_partition_for_geom() failed.

---

### Post by oldos2er on 2010-11-15
Which version of Ubuntu are you using? Can you post the output of ```
sudo fdisk -l
```

---

### Post by ByteOneZero on 2010-11-24
tenza@tenza-desktop:~$ sudo fdisk -l
[sudo] password for tenza: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe90be90b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19606   157480937    7  HPFS/NTFS
/dev/sda2           37756       38913     9301635    7  HPFS/NTFS
/dev/sda3           19606       37755   145784833    5  Extended
/dev/sda5           19606       37051   140127232   83  Linux
/dev/sda6           37051       37755     5656576   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4007 MB, 4007657472 bytes
86 heads, 22 sectors/track, 4137 cylinders
Units = cylinders of 1892 * 512 = 968704 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           5        4138     3909696    c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
1 heads, 63 sectors/track, 7752336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x008ca9b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           2     7752256   244196032+   7  HPFS/NTFS
tenza@tenza-desktop:~$ tenza@tenza-desktop:~$ sudo fdisk -l
tenza@tenza-desktop:~$: command not found
tenza@tenza-desktop:~$ [sudo] password for tenza: 
[sudo]: command not found
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$ Disk /dev/sda: 320.1 GB, 320072933376 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 255 heads, 63 sectors/track, 38913 cylinders
255: command not found
tenza@tenza-desktop:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
tenza@tenza-desktop:~$ Sector size (logical/physical): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ I/O size (minimum/optimal): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ Disk identifier: 0xe90be90b
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
tenza@tenza-desktop:~$ /dev/sda1   *           1       19606   157480937    7  HPFS/NTFS
bash: /dev/sda1: Permission denied
tenza@tenza-desktop:~$ /dev/sda2           37756       38913     9301635    7  HPFS/NTFS
bash: /dev/sda2: Permission denied
tenza@tenza-desktop:~$ /dev/sda3           19606       37755   145784833    5  Extended
bash: /dev/sda3: Permission denied
tenza@tenza-desktop:~$ /dev/sda5           19606       37051   140127232   83  Linux
bash: /dev/sda5: Permission denied
tenza@tenza-desktop:~$ /dev/sda6           37051       37755     5656576   82  Linux swap / Solaris
bash: /dev/sda6: Permission denied
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$ Partition table entries are not in disk order
Partition: command not found
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$ Disk /dev/sdb: 4007 MB, 4007657472 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 86 heads, 22 sectors/track, 4137 cylinders
86: command not found
tenza@tenza-desktop:~$ Units = cylinders of 1892 * 512 = 968704 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
tenza@tenza-desktop:~$ Sector size (logical/physical): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ I/O size (minimum/optimal): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ Disk identifier: 0xc3072e18
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
tenza@tenza-desktop:~$ /dev/sdb1   *           5        4138     3909696    c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$ Disk /dev/sdc: 250.1 GB, 250059350016 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 1 heads, 63 sectors/track, 7752336 cylinders
1: command not found
tenza@tenza-desktop:~$ Units = cylinders of 63 * 512 = 32256 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
tenza@tenza-desktop:~$ Sector size (logical/physical): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ I/O size (minimum/optimal): 512 bytes / 512 bytes
bash: syntax error near unexpected token `('
tenza@tenza-desktop:~$ Disk identifier: 0x008ca9b4
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
tenza@tenza-desktop:~$ /dev/sdc1   *           2     7752256   244196032+   7  HPFS/NTFS
bash: /dev/sdc1: Permission denied
tenza@tenza-desktop:~$ tenza@tenza-desktop:~$ 
tenza@tenza-desktop:~$: command not found
tenza@tenza-desktop:~$ 
gee ANN i am so dumb that i never found your response to my queary.ill wait to hear from you .or maybe this is so old ill need to send a private message.thank you regardless.

---

### Post by wojox on 2010-11-24
Still need version

```
uname -a
```

---

### Post by oldos2er on 2010-11-24
Are you running gparted from a LiveCD, or when you're booted to Ubuntu?

Also it looks like you have three hard drives, two of which may be somewhat old...? Can you tell us whether these drives are IDE or SATA?

---

### Post by ByteOneZero on 2010-11-24
lucid 10.04.and not from cd and my micro is brand new and empty.my seagate is 30 days old.my internal drive is pc age of 2.5 yrs.both are usb and 500 gb micro is sata.my ultimate goal is on another post,but it basically is to transfer all from internal to micro.wipe internal .reinstall win7 on internal hd.use my 250gb seagate for backups.put ubuntu on micro for a dual system.am i too ambitious for an ignorant noob?

---

