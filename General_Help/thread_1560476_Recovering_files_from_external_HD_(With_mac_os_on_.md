---
title: "Recovering files from external HD (With mac os on it)?"
date: 2010-08-24
forum: General Help
---

### Post by oyouareatubeo on 2010-08-24
Hello, thanks for reading this.

My powerbook died (motherboard or something...). I took out the Hard Drive to mount in an external enclosure.  I tried accessing the drive in both windows and mac - no luck. So, I thought I'd try it in Ubuntu, thinking maybe it would show up - no luck.  My question: is there any way to access the files from my drive using linux? Is there any way to mount it? The drive is spinning, and when I enter sudo fdisk -l ; I get this:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8cc64fb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         154     1228800    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             154       29127   232727548    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           29127       30402    10240000    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

[COLOR=Red]Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ad7e421[/COLOR]

This: [COLOR=Red]Disk /dev/sdb: 160.0 GB, 160041885696 bytes [COLOR=Black]is the drive I want to get my files off of.  So ubuntu is reading the drive in some fashion.

Thank you, and thank you.

-Tube
[/COLOR][/COLOR]

---

### Post by lmarmisa on 2010-08-24
According to the output of the command **sudo fdisk -l**, no partition is detected in your external HDD **/dev/sdb**. Is the output complete or maybe did you forget to include some lines?.

Try to use the partition editor program **GParted** ( **System -> Administration -> Gparted** ) in order to check if this program is able to detect some partition in your HDD. Install GParted with Synaptic if the partition editor is not installed in your system

Best regards,

Luis

---

### Post by lmarmisa on 2010-08-24
It would be interesting to know the contents of the [Master Boot Record MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of your external HDD.

Open a terminal and type this command:

> 
sudo dd bs=512 count=1 if=/dev/sdb | xxd
This is the output for my /dev/sda HDD:

```

luis@UB1004ENG:~/Desktop$ sudo dd bs=512 count=1 if=/dev/sda | xxd
0000000: eb63 9010 8ed0 bc00 b0b8 0000 8ed8 8ec0  .c..............
0000010: fbbe 007c bf00 06b9 0002 f3a4 ea21 0600  ...|.........!..
0000020: 00be be07 3804 750b 83c6 1081 fefe 0775  ....8.u........u
0000030: f3eb 16b4 02b0 01bb 007c b280 8a74 018b  .........|...t..
0000040: 4c02 cd13 ea00 7c00 00eb fe00 0000 0000  L.....|.........
0000050: 0000 0000 0000 0000 0000 0080 0100 0000  ................
0000060: 0000 0000 fffa 9090 f6c2 8075 02b2 80ea  ...........u....
0000070: 747c 0000 31c0 8ed8 8ed0 bc00 20fb a064  t|..1....... ..d
0000080: 7c3c ff74 0288 c252 bb17 0480 2703 7406  |<.t...R....'.t.
0000090: be88 7de8 1c01 be05 7cf6 c280 7448 b441  ..}.....|...tH.A
00000a0: bbaa 55cd 135a 5272 3d81 fb55 aa75 3783  ..U..ZRr=..U.u7.
00000b0: e101 7432 31c0 8944 0440 8844 ff89 4402  ..t21..D.@.D..D.
00000c0: c704 1000 668b 1e5c 7c66 895c 0866 8b1e  ....f..\|f.\.f..
00000d0: 607c 6689 5c0c c744 0600 70b4 42cd 1372  `|f.\..D..p.B..r
00000e0: 05bb 0070 eb76 b408 cd13 730d f6c2 800f  ...p.v....s.....
00000f0: 84d0 00be 937d e982 0066 0fb6 c688 64ff  .....}...f....d.
0000100: 4066 8944 040f b6d1 c1e2 0288 e888 f440  @f.D...........@
0000110: 8944 080f b6c2 c0e8 0266 8904 66a1 607c  .D.......f..f.`|
0000120: 6609 c075 4e66 a15c 7c66 31d2 66f7 3488  f..uNf.\|f1.f.4.
0000130: d131 d266 f774 043b 4408 7d37 fec1 88c5  .1.f.t.;D.}7....
0000140: 30c0 c1e8 0208 c188 d05a 88c6 bb00 708e  0........Z....p.
0000150: c331 dbb8 0102 cd13 721e 8cc3 601e b900  .1......r...`...
0000160: 018e db31 f6bf 0080 8ec6 fcf3 a51f 61ff  ...1..........a.
0000170: 265a 7cbe 8e7d eb03 be9d 7de8 3400 bea2  &Z|..}....}.4...
0000180: 7de8 2e00 cd18 ebfe 4752 5542 2000 4765  }.......GRUB .Ge
0000190: 6f6d 0048 6172 6420 4469 736b 0052 6561  om.Hard Disk.Rea
00001a0: 6400 2045 7272 6f72 0d0a 00bb 0100 b40e  d. Error........
00001b0: cd10 ac3c 0075 f4c3 3ece 0400 0000 8020  ...<.u..>...... 
00001c0: 2100 8356 f5e1 0008 0000 0078 f300 0077  !..V.......x...w
00001d0: d5e1 05fe ffff fe87 f300 0270 0c00 0000  ...........p....
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00225332 s, 227 kB/s
luis@UB1004ENG:~/Desktop$

```The most important information to check is the Table of primary partitions (four 16-bytes entries located from the address 0001be).

---

