---
title: "Strange zero entries in partition table and gparted not accurate...how to fix?"
date: 2009-12-22
forum: General Help
---

### Post by tedrogers on 2009-12-22
Hi,

I started looking into this issue because gparted wasn't showing me accurate information for a USB hard drive, i.e. I know the hard disk is 640GB in size but gparted was only telling me that 320gb existed, and it didn't know the file system type when I know it is FAT32.

So I did some digging around and looked at my partitions using:

```
sudo sfdisk -d
```

...which produces this output:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20964762, Id=83, bootable
/dev/sda2 : start= 94124835, size=  2104515, Id=82
/dev/sda3 : start= 96229350, size= 20980890, Id= 5
/dev/sda4 : start= 20964825, size= 73160010, Id=83
/dev/sda5 : start= 96229413, size= 20980827, Id=83

# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=625121217, Id= c
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
```

Now, the only thing that looks wrong here is all those zero entries for sdb2, sdb3 etc. Everything else is as I expect it.

How can I fix these zero entries? I think they are causing problems with other removable media like SD cards too.

Thanks.

---

### Post by dcstar on 2009-12-22
> **tedrogers said:**
> Hi,

I started looking into this issue because gparted wasn't showing me accurate information for a USB hard drive, i.e. I know the hard disk is 640GB in size but gparted was only telling me that 320gb existed, and it didn't know the file system type when I know it is FAT32.

So I did some digging around and looked at my partitions using:

```
sudo sfdisk -d
```

...which produces this output:

```

# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=625121217, Id= c
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
```

Now, the only thing that looks wrong here is all those zero entries for sdb2, sdb3 etc. Everything else is as I expect it.

How can I fix these zero entries? I think they are causing problems with other removable media like SD cards too.


Move the data off the working partition and use gparted to write a fresh partition table, then format a new partition and copy the data back on to it.

---

### Post by tedrogers on 2009-12-22
Hmmm...when I try to create a new partition, this is what happens!

```
======================
libparted : 1.8.8.1.159-1e0e
======================
Device /dev/sdb has a logical sector size of 1024.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Cannot have a partition outside the disk!
Device /dev/sdb has a logical sector size of 1024.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Cannot have a partition outside the disk!
*** stack smashing detected ***: /usr/sbin/gpartedbin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xd0dde8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xd0dda0]
/lib/libparted-1.8.so.12[0xe21104]
/lib/libparted-1.8.so.12[0xe0d1b3]
[0x0]
======= Memory map: ========
00110000-00150000 r-xp 00000000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00150000-00151000 ---p 00040000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00151000-00154000 r--p 00040000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00154000-00155000 rw-p 00043000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00155000-00180000 r-xp 00000000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00180000-00181000 r--p 0002b000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00181000-00182000 rw-p 0002c000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00182000-001d7000 r-xp 00000000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d7000-001d8000 ---p 00055000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d8000-001d9000 r--p 00055000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d9000-001da000 rw-p 00056000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001da000-0026c000 r-xp 00000000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026c000-0026e000 r--p 00092000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026e000-0026f000 rw-p 00094000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026f000-00287000 r-xp 00000000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00287000-00288000 r--p 00017000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00288000-00289000 rw-p 00018000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00289000-002a4000 r-xp 00000000 08:01 180908     /lib/ld-2.10.1.so
002a4000-002a5000 r--p 0001a000 08:01 180908     /lib/ld-2.10.1.so
002a5000-002a6000 rw-p 0001b000 08:01 180908     /lib/ld-2.10.1.so
002a6000-002c1000 r-xp 00000000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c1000-002c2000 r--p 0001b000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c2000-002c3000 rw-p 0001c000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c3000-002ea000 r-xp 00000000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002ea000-002eb000 r--p 00027000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002eb000-002ec000 rw-p 00028000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002ec000-002f7000 r-xp 00000000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f7000-002f8000 r--p 0000a000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f8000-002f9000 rw-p 0000b000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f9000-002fc000 r-xp 00000000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fc000-002fd000 r--p 00002000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fd000-002fe000 rw-p 00003000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fe000-00300000 r-xp 00000000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00300000-00301000 r--p 00001000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00301000-00302000 rw-p 00002000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00302000-00305000 r-xp 00000000 08:01 180827     /lib/libuuid.so.1.3.0
00305000-00306000 r--p 00002000 08:01 180827     /lib/libuuid.so.1.3.0
00306000-00307000 rw-p 00003000 08:01 180827     /lib/libuuid.so.1.3.0
00307000-0030e000 r-xp 00000000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
0030e000-0030f000 r--p 00006000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
0030f000-00310000 rw-p 00007000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
00310000-00318000 r-xp 00000000 08:01 623913     /usr/lib/libXrender.so.1.3.0
00318000-00319000 r--p 00007000 08:01 623913     /usr/lib/libXrender.so.1.3.0
00319000-0031a000 rw-p 00008000 08:01 623913     /usr/lib/libXrender.so.1.3.0
0031a000-0031c000 r-xp 00000000 08:01 287033     /usr/lib/libXdamage.so.1.1.0
0031c000-0031d000 rw-p 00001000 08:01 287033     /usr/lib/libXdamage.so.1.1.0
0031d000-0033c000 r-xp 00000000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033c000-0033d000 r--p 0001e000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033d000-0033e000 rw-p 0001f000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033e000-003d1000 r-xp 00000000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d1000-003d2000 r--p 00092000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d2000-003d3000 rw-p 00093000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d3000-003d4000 rw-p 00000000 00:00 0 
003d4000-0041a000 r-xp 00000000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041a000-0041b000 r--p 00045000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041b000-0041c000 rw-p 00046000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041c000-00440000 r-xp 00000000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00440000-00441000 r--p 00023000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00441000-00442000 rw-p 00024000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00443000-00447000 r-xp 00000000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00447000-00448000 r--p 00003000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00448000-00449000 rw-p 00004000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00449000-004cd000 r-xp 00000000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004cd000-004cf000 r--p 00083000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004cf000-004d0000 rw-p 00085000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004d0000-004d2000 r-xp 00000000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d2000-004d3000 r--p 00001000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d3000-004d4000 rw-p 00002000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d4000-004d8000 r-xp 00000000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004d8000-004d9000 r--p 00003000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004d9000-004da000 rw-p 00004000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004da000-004dc000 r-xp 00000000 08:01 624855     /usr/lib/libXinerama.so.1.0.0
004dc000-004dd000 rw-p 00001000 08:01 624855     /usr/lib/libXinerama.so.1.0.0
004dd000-004e0000 r-xp 00000000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e0000-004e1000 r--p 00002000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e1000-004e2000 rw-p 00003000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e2000-004e7000 r-xp 00000000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e7000-004e8000 r--p 00004000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e8000-004e9000 rw-p 00005000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e9000-00563000 r-xp 00000000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00563000-00567000 r--p 00079000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00567000-00568000 rw-p 0007d000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00568000-00593000 r-xp 00000000 08:01 286852     /usr/lib/libfontconfig.so.1.3.0
00593000-00594000 r--p 0002a000 08:01 286852     /usr/lib/libfontconfig.so.1.3.0
```

That bit about STACK SMASHING doesn't sound good.

Just a note, that this a preformatted by the manufacturer. Guess I might have to stick it on a Windows machine to sort this out, but I shouldn't have to really should I?

Thanks for you help so far.

---

### Post by AgentZ86 on 2009-12-22
/dev/sdb1 : start=       63, size=625121217, Id= c

If this is correct ?

Then the others should be 0 because there is no more space left as it's already been allocated.

But if this is not correct, and this partition sdb1 is smaller then your full capacity of 640GB then something is wrong

Also the ID=c I'm not sure which selections that is typically the fdisk has ID's like numbers mostly ?

How are you booting the machine from the hard drive sda1 ? or from the gparted bootable live CD ?

The gparted live CD is the best method and you could try unplugging the sda1 just to diagnose this again.

You want to make sure the drive is unmounted when you test with gparted ?

Anyhow thats about all I can think of right now anyhow.
Hope this helps

---

### Post by AgentZ86 on 2009-12-22
> **tedrogers said:**
> Hmmm...when I try to create a new partition, this is what happens!

```
======================
libparted : 1.8.8.1.159-1e0e
======================
Device /dev/sdb has a logical sector size of 1024.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Cannot have a partition outside the disk!
Device /dev/sdb has a logical sector size of 1024.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Cannot have a partition outside the disk!
*** stack smashing detected ***: /usr/sbin/gpartedbin terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xd0dde8]
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)[0xd0dda0]
/lib/libparted-1.8.so.12[0xe21104]
/lib/libparted-1.8.so.12[0xe0d1b3]
[0x0]
======= Memory map: ========
00110000-00150000 r-xp 00000000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00150000-00151000 ---p 00040000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00151000-00154000 r--p 00040000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00154000-00155000 rw-p 00043000 08:01 623817     /usr/lib/libatkmm-1.6.so.1.1.0
00155000-00180000 r-xp 00000000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00180000-00181000 r--p 0002b000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00181000-00182000 rw-p 0002c000 08:01 623013     /usr/lib/libpangomm-1.4.so.1.0.30
00182000-001d7000 r-xp 00000000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d7000-001d8000 ---p 00055000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d8000-001d9000 r--p 00055000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001d9000-001da000 rw-p 00056000 08:01 624663     /usr/lib/libglibmm-2.4.so.1.2.0
001da000-0026c000 r-xp 00000000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026c000-0026e000 r--p 00092000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026e000-0026f000 rw-p 00094000 08:01 624240     /usr/lib/libgdk-x11-2.0.so.0.1800.3
0026f000-00287000 r-xp 00000000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00287000-00288000 r--p 00017000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00288000-00289000 rw-p 00018000 08:01 624245     /usr/lib/libgdk_pixbuf-2.0.so.0.1800.3
00289000-002a4000 r-xp 00000000 08:01 180908     /lib/ld-2.10.1.so
002a4000-002a5000 r--p 0001a000 08:01 180908     /lib/ld-2.10.1.so
002a5000-002a6000 rw-p 0001b000 08:01 180908     /lib/ld-2.10.1.so
002a6000-002c1000 r-xp 00000000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c1000-002c2000 r--p 0001b000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c2000-002c3000 rw-p 0001c000 08:01 622798     /usr/lib/libatk-1.0.so.0.2809.1
002c3000-002ea000 r-xp 00000000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002ea000-002eb000 r--p 00027000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002eb000-002ec000 rw-p 00028000 08:01 624701     /usr/lib/libpangoft2-1.0.so.0.2600.0
002ec000-002f7000 r-xp 00000000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f7000-002f8000 r--p 0000a000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f8000-002f9000 rw-p 0000b000 08:01 624627     /usr/lib/libpangocairo-1.0.so.0.2600.0
002f9000-002fc000 r-xp 00000000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fc000-002fd000 r--p 00002000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fd000-002fe000 rw-p 00003000 08:01 624978     /usr/lib/libgmodule-2.0.so.0.2200.3
002fe000-00300000 r-xp 00000000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00300000-00301000 r--p 00001000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00301000-00302000 rw-p 00002000 08:01 573466     /lib/tls/i686/cmov/libdl-2.10.1.so
00302000-00305000 r-xp 00000000 08:01 180827     /lib/libuuid.so.1.3.0
00305000-00306000 r--p 00002000 08:01 180827     /lib/libuuid.so.1.3.0
00306000-00307000 rw-p 00003000 08:01 180827     /lib/libuuid.so.1.3.0
00307000-0030e000 r-xp 00000000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
0030e000-0030f000 r--p 00006000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
0030f000-00310000 rw-p 00007000 08:01 573484     /lib/tls/i686/cmov/librt-2.10.1.so
00310000-00318000 r-xp 00000000 08:01 623913     /usr/lib/libXrender.so.1.3.0
00318000-00319000 r--p 00007000 08:01 623913     /usr/lib/libXrender.so.1.3.0
00319000-0031a000 rw-p 00008000 08:01 623913     /usr/lib/libXrender.so.1.3.0
0031a000-0031c000 r-xp 00000000 08:01 287033     /usr/lib/libXdamage.so.1.1.0
0031c000-0031d000 rw-p 00001000 08:01 287033     /usr/lib/libXdamage.so.1.1.0
0031d000-0033c000 r-xp 00000000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033c000-0033d000 r--p 0001e000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033d000-0033e000 rw-p 0001f000 08:01 624122     /usr/lib/libcairomm-1.0.so.1.3.0
0033e000-003d1000 r-xp 00000000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d1000-003d2000 r--p 00092000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d2000-003d3000 rw-p 00093000 08:01 624997     /usr/lib/libgio-2.0.so.0.2200.3
003d3000-003d4000 rw-p 00000000 00:00 0 
003d4000-0041a000 r-xp 00000000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041a000-0041b000 r--p 00045000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041b000-0041c000 rw-p 00046000 08:01 624545     /usr/lib/libpango-1.0.so.0.2600.0
0041c000-00440000 r-xp 00000000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00440000-00441000 r--p 00023000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00441000-00442000 rw-p 00024000 08:01 573467     /lib/tls/i686/cmov/libm-2.10.1.so
00443000-00447000 r-xp 00000000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00447000-00448000 r--p 00003000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00448000-00449000 rw-p 00004000 08:01 624994     /usr/lib/libgthread-2.0.so.0.2200.3
00449000-004cd000 r-xp 00000000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004cd000-004cf000 r--p 00083000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004cf000-004d0000 rw-p 00085000 08:01 623991     /usr/lib/libcairo.so.2.10800.8
004d0000-004d2000 r-xp 00000000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d2000-004d3000 r--p 00001000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d3000-004d4000 rw-p 00002000 08:01 624277     /usr/lib/libXcomposite.so.1.0.0
004d4000-004d8000 r-xp 00000000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004d8000-004d9000 r--p 00003000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004d9000-004da000 rw-p 00004000 08:01 624842     /usr/lib/libXfixes.so.3.1.0
004da000-004dc000 r-xp 00000000 08:01 624855     /usr/lib/libXinerama.so.1.0.0
004dc000-004dd000 rw-p 00001000 08:01 624855     /usr/lib/libXinerama.so.1.0.0
004dd000-004e0000 r-xp 00000000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e0000-004e1000 r--p 00002000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e1000-004e2000 rw-p 00003000 08:01 623774     /usr/lib/libxcb-render-util.so.0.0.0
004e2000-004e7000 r-xp 00000000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e7000-004e8000 r--p 00004000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e8000-004e9000 rw-p 00005000 08:01 624231     /usr/lib/libsigc-2.0.so.0.0.0
004e9000-00563000 r-xp 00000000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00563000-00567000 r--p 00079000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00567000-00568000 rw-p 0007d000 08:01 623449     /usr/lib/libfreetype.so.6.3.20
00568000-00593000 r-xp 00000000 08:01 286852     /usr/lib/libfontconfig.so.1.3.0
00593000-00594000 r--p 0002a000 08:01 286852     /usr/lib/libfontconfig.so.1.3.0
```

That bit about STACK SMASHING doesn't sound good.

Just a note, that this a preformatted by the manufacturer. Guess I might have to stick it on a Windows machine to sort this out, but I shouldn't have to really should I?

Thanks for you help so far.

What type partition were you trying to create ? 

You could try creating a ext3 partition this will wipe things out for you then once you format and restart you can then check out the drive, after that you could then try to create a FAT32 and try that again and see if you get the same message or success this time.

---

### Post by tedrogers on 2009-12-23
Well, it's one of these drives, except the latest newest 640GB version.

[http://www.samsung.com/sg/consumer/pc-peripherals-printer/hard-disk-drive/external-storage/HXMU050DA/K22/index.idx?pagetype=prd_detail]("http://www.samsung.com/sg/consumer/pc-peripherals-printer/hard-disk-drive/external-storage/HXMU050DA/K22/index.idx?pagetype=prd_detail")

It came preformatted to FAT32, which shows as 630GB when you check the preferences for the drive icon, but gparted shows it as half that size! fdisk reports it is the proper size, but behaves erratically when creating partitions as well.

I was trying to create a basic ext2 partition to wipe it all off and then put it to NTFS, so I have large file support across different platforms.

I've failed with gparted so far (in Ubuntu and System Rescue CD). Works fine in Win and Mac. It's silly! :(

Tell you what though, I think there may be some kind of boot-block code installed on it, because I cannot for the life of me, on any OS, change the drive name from anything other than SAMSUNG.

---

### Post by dcstar on 2009-12-23
> **tedrogers said:**
> Hmmm...when I try to create a new partition, this is what happens!
......

Did you use gparted to create a** new partition table**?

---

### Post by tedrogers on 2009-12-23
> **dcstar said:**
> Did you use gparted to create a** new partition table**?

It fails to create a partition.

The worrying thing is that this message appears for libparted.

```
Device /dev/sdb has a logical sector size of 1024.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.

Cannot have a partition outside the disk!
```

I've formatted it on a windows machine now to NTFS...but I'm still none the wiser as to why gparted doesn't report the proper size. I expect it's due to the HIGHLY EXPERIMENTAL nature of using a disk with a sector size of 1024....whatever that means! And why gparted should be goosed by this particular drive I have no idea.

---

