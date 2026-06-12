---
title: "Grub &quot;Invalid Signature&quot;"
date: 2010-06-07
forum: General Help
---

### Post by watersa8 on 2010-06-07
Hey i did a fresh install of windows and then ubuntu and seem to be having some problems with grub i have tried some of the fixes which were suggested on 
[http://ubuntuforums.org/showthread.php?t=1264151](http://ubuntuforums.org/showthread.php?t=1264151)
to no avail

on a side note i did have this problem before after a ubuntu update grub just stopped letting me access windows with the same error message and as stated i did do a fresh install so theres nothign wrogn with windows or ubuntu which leads me to believe the problem is with grub itself and on this subject i am completely clueless :s

when i try to run sudo os-prober it only shows my windows partition

```

watersa8@watersa8-desktop:~$ sudo os-prober
/dev/sdb1:Microsoft Windows XP Professional:Windows:chain
watersa8@watersa8-desktop:~$

``` 

i also get errors when running sudo update-grub

```

watersa8@watersa8-desktop:~$ sudo update-grub
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
Generating grub.cfg ...
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
Found memtest86+ image: /boot/memtest86+.bin
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
Found Microsoft Windows XP Professional on /dev/sdb1
error: cannot seek `/dev/sdc'.
error: cannot seek `/dev/sdc'.
/usr/sbin/grub-probe: error: unknown filesystem.
done
watersa8@watersa8-desktop:~$ 

```

i dont know why i get the error with sdc its just a hard drive i use for storage and doesnt contain either os so it can be ignored Im guessing that the unknown filesystem must be ubuntu which i cant figure out y it cant recognize that as ubuntu is the os which installed grub.....

Other things which may be useful in solving the problem...

fdisk-l report

```

watersa8@watersa8-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6932eff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      182401  1465136001   42  SFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa331a332

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           12749       30516   142717953    5  Extended
/dev/sdb5           12749       13496     5999616   82  Linux swap / Solaris
/dev/sdb6           13496       30516   136717312   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x848981b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001   42  SFS

```

sudo dmesg | grep sd[abc]

```

watersa8@watersa8-desktop:~$ sudo dmesg | grep sd[abc]
[    2.256418] sd 6:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.256449] sd 6:0:0:0: [sda] Write Protect is off
[    2.256451] sd 6:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.256467] sd 6:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.256563]  sda:
[    2.261001]  sda1
[    2.261257] sd 6:0:0:0: [sda] Attached SCSI disk
[    2.568851] sd 8:0:0:0: [sdb] 490234752 512-byte logical blocks: (251 GB/233 GiB)
[    2.568879] sd 8:0:0:0: [sdb] Write Protect is off
[    2.568881] sd 8:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.568897] sd 8:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.568975]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    2.610438] sd 8:0:0:0: [sdb] Attached SCSI disk
[    2.954808] EXT4-fs (sdb6): mounted filesystem with ordered data mode
[    3.052572] sd 9:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    3.052604] sd 9:0:0:0: [sdc] Write Protect is off
[    3.052607] sd 9:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.052623] sd 9:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.052724]  sdc: [LDM] sdc1
[    3.110536] sd 9:0:0:0: [sdc] Attached SCSI disk
[   10.363377] Adding 5999608k swap on /dev/sdb5.  Priority:-1 extents:1 across:5999608k 
[  275.705161] sd 8:0:0:0: [sdb] Unhandled sense code
[  275.705163] sd 8:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  275.705166] sd 8:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  275.705182] sd 8:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  275.705186] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 47 00 00 10 00
[  275.705193] end_request: I/O error, dev sdb, sector 6291540
[  275.705199] Buffer I/O error on device sdb1, logical block 6291477
[  275.705202] Buffer I/O error on device sdb1, logical block 6291478
[  275.705205] Buffer I/O error on device sdb1, logical block 6291479
[  715.481130] sd 8:0:0:0: [sdb] Unhandled sense code
[  715.481132] sd 8:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  715.481136] sd 8:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  715.481152] sd 8:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  715.481156] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 47 00 00 10 00
[  715.481163] end_request: I/O error, dev sdb, sector 6291540
[  715.481166] Buffer I/O error on device sdb1, logical block 6291477
[  715.481169] Buffer I/O error on device sdb1, logical block 6291478
[  715.481172] Buffer I/O error on device sdb1, logical block 6291479
[  736.765140] sd 8:0:0:0: [sdb] Unhandled sense code
[  736.765142] sd 8:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  736.765145] sd 8:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  736.765161] sd 8:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  736.765166] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 4f 00 00 10 00
[  736.765172] end_request: I/O error, dev sdb, sector 6291540
[  736.765176] Buffer I/O error on device sdb1, logical block 6291477
[  736.765179] Buffer I/O error on device sdb1, logical block 6291478
[  736.765182] Buffer I/O error on device sdb1, logical block 6291479
[  736.765187] Buffer I/O error on device sdb1, logical block 6291480
[  736.765189] Buffer I/O error on device sdb1, logical block 6291481
[  736.765192] Buffer I/O error on device sdb1, logical block 6291482
[  736.765195] Buffer I/O error on device sdb1, logical block 6291483
[  736.765197] Buffer I/O error on device sdb1, logical block 6291484
[  736.765200] Buffer I/O error on device sdb1, logical block 6291485
[  736.765202] Buffer I/O error on device sdb1, logical block 6291486
[  756.165144] sd 8:0:0:0: [sdb] Unhandled sense code
[  756.165146] sd 8:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  756.165150] sd 8:0:0:0: [sdb] Sense Key : Medium Error [current] [descriptor]
[  756.165165] sd 8:0:0:0: [sdb] Add. Sense: Unrecovered read error - auto reallocate failed
[  756.165170] sd 8:0:0:0: [sdb] CDB: Read(10): 28 00 00 60 00 54 00 00 03 00
[  756.165176] end_request: I/O error, dev sdb, sector 6291540
[  756.165183] Buffer I/O error on device sdb1, logical block 6291477
[  756.165186] Buffer I/O error on device sdb1, logical block 6291478
[  756.165189] Buffer I/O error on device sdb1, logical block 6291479

```

If theres anything else anybody needs to see just ask
Thanks in advance

---

### Post by watersa8 on 2010-06-07
I just reinstalled both os's again with only the 1 hard drive connected thinkign the problem may lie with my 3rd hard drive for some inexplicable reason but sadly no luck i still get the invalid signature message when trying to accexx windows xp via grub anyone got any ideas or had the same problem and knows how to solve it?

One further thing when reinstalling i got the error message 
"Sorry, an error occurred and it was not possible to install bootloader at the specified location"
I did get this before but it wouldnt install to either of the other 2 hard drives either but when i restarted i got to the grub screen fine....

---

### Post by watersa8 on 2010-06-12
/bump

---

### Post by dino99 on 2010-06-12
/dev/sdc1  [COLOR="Red"] *  [/COLOR]         1      121601   976760001   42  SFS

why is it [COLOR="Red"]bootable[/COLOR] and what is that[COLOR="Red"] SFS [/COLOR]filesystem ?

check the partitions with [http://partedmagic.com/](http://partedmagic.com/)

[http://manpages.ubuntu.com/manpages/jaunty/en/man7/sfs.7.html](http://manpages.ubuntu.com/manpages/jaunty/en/man7/sfs.7.html)

---

### Post by watersa8 on 2010-06-12
sdc1 and sda1 are just a hard drives for storing files there isnt anything which can be booted from at that location as for the sfs i arnt sure y its stated it as that as it is partitioned in ntfs format through windows xp

---

### Post by dino99 on 2010-06-12
> **watersa8 said:**
> sdc1 and sda1 are just a hard drives for storing files there isnt anything which can be booted from at that location as for the sfs i arnt sure y its stated it as that as it is partitioned in [COLOR="Blue"]ntfs format through windows xp[/COLOR]

[COLOR="Red"]surely not[/COLOR]

---

