---
title: "Recover lost partitions"
date: 2011-11-14
forum: General Help
---

### Post by h1volt3 on 2011-11-14
After a Windows crash (likely to be a hardware failure because no disks were detected in several subsequent boots), all of my Linux partition were gone. I tried testdisk and managed to recover most of my partition, except /home, which was on /dev/sda6. gparted reports it as an unknown filesystem. dumpe2fs output:
```
dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda6
Couldn't find valid filesystem superblock.
```

I'm using photorec to recover the files on /home, but the paths of files aren't preserved. Since there is (hopefully) no write to disk after the crash, I think that the problem can be better solved by figuring out the correct start and end offsets of the partitions so that I can mount them as if there was no problem ever happened. Is that right? Are there any other tools to recover correct partition table? I tried gpart but it's not helpful. Here is its output:
```
Begin scan...
Possible extended partition at offset(50007mb)
   Possible partition(Linux swap), size(2039mb), offset(50007mb)
   Possible partition(Linux ext2), size(8189mb), offset(62283mb)
   Possible partition(Windows NT/W2K FS), size(400543mb), offset(70472mb)
   Possible partition(Windows NT/W2K FS), size(5914mb), offset(471023mb)
End scan.

Checking partitions...

* Warning: more than one extended partition: 2.
   Partition(Linux swap or Solaris/x86): invalid logical 
Partition(Linux ext2 filesystem): invalid 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): invalid 
Partition(OS/2 HPFS, NTFS, QNX or Advanced UNIX): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 015(0x0F)(Extended DOS, LBA)
   size: 20465mb #s(41913580) s(102414375-144327954)
   chs:  (1023/254/63)-(1023/254/63)d (6375/0/1)-(8983/254/58)r

Primary partition(2)
   type: 007(0x07)(OS/2 HPFS, NTFS, QNX or Advanced UNIX)
   size: 5914mb #s(12112947) s(964655118-976768064)
   chs:  (1023/254/63)-(1023/254/63)d (60047/1/1)-(60800/254/63)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```


Some output:

```
fdisk -l /dev/sda
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe33c7df6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102399999    51096576    7  HPFS/NTFS/exFAT
/dev/sda3       102414375   976768064   437176845    f  W95 Ext'd (LBA)
/dev/sda5       102414438   106591253     2088408   82  Linux swap / Solaris
/dev/sda6       106591338   127556097    10482380   83  Linux
/dev/sda7       127556163   144327954     8385896   83  Linux
/dev/sda8       144328023   964640511   410156244+   7  HPFS/NTFS/exFAT
/dev/sda9       964655118   976768064     6056473+   7  HPFS/NTFS/exFAT

```

Partition table reported by teskdisk seems weird. Here it is
```
Disk /dev/sda - 500 GB / 465 GiB (RO) - ATA ST3500418AS

     Partition                  Start        End    Size in sectors
     No partition             0   0  1 60801  80 63  976773168 [Whole disk]
 1 * HPFS - NTFS              0  32 33    12 223 19     204800 [System Reserved]
 2 P HPFS - NTFS             12 223 20  6374  26 52  102193152
 3 E extended LBA          6375   0  1 60800 254 63  874353690
 5 L Linux Swap            6375   1  1  6634 254 42    4176816
   X extended              6635   0  1  7939 254 61   20964823
 6 L Linux                 6635   1  1  7939 254 61   20964760
   X extended              7940   0  1  8983 254 58   16771855
 7 L Linux                 7940   1  1  8983 254 58   16771792
   X extended              8984   0  1 60046  24 10  820312552
 8 L HPFS - NTFS           8984   1  1 60046  24 10  820312489
   X extended             60047   0  1 60800 254 63   12113010
 9 L HPFS - NTFS          60047   1  1 60800 254 63   12112947

```

Any help is appreciated. Thanks! :)

---

