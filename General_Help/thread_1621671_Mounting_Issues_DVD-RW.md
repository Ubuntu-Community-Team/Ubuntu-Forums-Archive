---
title: "Mounting Issues DVD-RW"
date: 2010-11-14
forum: General Help
---

### Post by johnsky on 2010-11-14
Having some troubles mounting my DVD-RW after a reinstall of ubuntu. Now using 10.10.

Follow my hole ridden logic with me and tell me where I'm screwing up.

```

root@Johnsky:/# wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/scd0'	rwrw-- : 'HL-DT-ST' 'DVDRAM GH20NS10'
-------------------------------------------------------------------------

```

So there's my scd0 sitting pretty.
Trying to mount it.

```

root@Johnsky:/# mount -a /dev/scd0 /media/cdrom0
mount: /dev/sr0: unknown device
root@Johnsky:/# 

```

sr0?

```

root@Johnsky:/# ls -l /dev/
total 0
crw-------  1 root root     10, 235 2010-11-14 13:25 autofs
drwxr-xr-x  2 root root         660 2010-11-14 13:25 block
drwxr-xr-x  2 root root          80 2010-11-14 08:24 bsg
crw-------  1 root root     10, 234 2010-11-14 13:25 btrfs-control
drwxr-xr-x  3 root root          60 2010-11-14 08:24 bus
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 cdrw -> sr0
drwxr-xr-x  2 root root        2980 2010-11-14 13:25 char
crw-------  1 root root      5,   1 2010-11-14 13:25 console
lrwxrwxrwx  1 root root          11 2010-11-14 13:25 core -> /proc/kcore
drwxr-xr-x  2 root root          60 2010-11-14 13:25 cpu
crw-------  1 root root     10,  58 2010-11-14 13:25 cpu_dma_latency
drwxr-xr-x  5 root root         100 2010-11-14 08:24 disk
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 dvd -> sr0
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 dvdrw -> sr0
crw-------  1 root root     10,  61 2010-11-14 13:25 ecryptfs
lrwxrwxrwx  1 root root          13 2010-11-14 13:25 fd -> /proc/self/fd
brw-rw----  1 root floppy    2,   0 2010-11-14 13:25 fd0
brw-rw----  1 root floppy    2,  84 2010-11-14 13:25 fd0u1040
brw-rw----  1 root floppy    2,  88 2010-11-14 13:25 fd0u1120
brw-rw----  1 root floppy    2,  28 2010-11-14 13:25 fd0u1440
brw-rw----  1 root floppy    2, 124 2010-11-14 13:25 fd0u1600
brw-rw----  1 root floppy    2,  44 2010-11-14 13:25 fd0u1680
brw-rw----  1 root floppy    2,  60 2010-11-14 13:25 fd0u1722
brw-rw----  1 root floppy    2,  76 2010-11-14 13:25 fd0u1743
brw-rw----  1 root floppy    2,  96 2010-11-14 13:25 fd0u1760
brw-rw----  1 root floppy    2, 116 2010-11-14 13:25 fd0u1840
brw-rw----  1 root floppy    2, 100 2010-11-14 13:25 fd0u1920
brw-rw----  1 root floppy    2,  12 2010-11-14 13:25 fd0u360
brw-rw----  1 root floppy    2,  16 2010-11-14 13:25 fd0u720
brw-rw----  1 root floppy    2, 120 2010-11-14 13:25 fd0u800
brw-rw----  1 root floppy    2,  52 2010-11-14 13:25 fd0u820
brw-rw----  1 root floppy    2,  68 2010-11-14 13:25 fd0u830
crw-rw-rw-  1 root root      1,   7 2010-11-14 13:25 full
crw-rw-rw-  1 root fuse     10, 229 2010-11-14 13:25 fuse
crw-------  1 root root     10, 228 2010-11-14 13:25 hpet
drwxr-xr-x  3 root root         180 2010-11-14 13:25 input
crw-------  1 root root      1,  11 2010-11-14 13:25 kmsg
srw-rw-rw-  1 root root           0 2010-11-14 13:25 log
brw-rw----  1 root disk      7,   0 2010-11-14 13:25 loop0
brw-rw----  1 root disk      7,   1 2010-11-14 13:25 loop1
brw-rw----  1 root disk      7,   2 2010-11-14 13:25 loop2
brw-rw----  1 root disk      7,   3 2010-11-14 13:25 loop3
brw-rw----  1 root disk      7,   4 2010-11-14 13:25 loop4
brw-rw----  1 root disk      7,   5 2010-11-14 13:25 loop5
brw-rw----  1 root disk      7,   6 2010-11-14 13:25 loop6
brw-rw----  1 root disk      7,   7 2010-11-14 13:25 loop7
crw-rw----  1 root lp        6,   0 2010-11-14 13:25 lp0
drwxr-xr-x  2 root root          60 2010-11-14 08:24 mapper
crw-------  1 root root     10, 227 2010-11-14 13:25 mcelog
crw-r-----  1 root kmem      1,   1 2010-11-14 13:25 mem
drwxr-xr-x  2 root root          60 2010-10-25 23:30 net
crw-------  1 root root     10,  57 2010-11-14 13:25 network_latency
crw-------  1 root root     10,  56 2010-11-14 13:25 network_throughput
crw-rw-rw-  1 root root      1,   3 2010-11-14 13:25 null
crw-rw-rw-  1 root root    195,   0 2010-11-14 13:25 nvidia0
crw-rw-rw-  1 root root    195, 255 2010-11-14 13:25 nvidiactl
crw-------  1 root root      1,  12 2010-11-14 13:25 oldmem
crw-rw----  1 root lp       99,   0 2010-11-14 13:25 parport0
drwxr-xr-x  2 root root          60 2010-11-14 08:24 pktcdvd
crw-r-----  1 root kmem      1,   4 2010-11-14 13:25 port
crw-------  1 root root    108,   0 2010-11-14 13:25 ppp
crw-------  1 root root     10,   1 2010-11-14 13:25 psaux
crw-rw-rw-  1 root tty       5,   2 2010-11-14 13:45 ptmx
drwxr-xr-x  2 root root           0 2010-09-24 08:25 pts
brw-rw----  1 root disk      1,   0 2010-11-14 13:25 ram0
brw-rw----  1 root disk      1,   1 2010-11-14 13:25 ram1
brw-rw----  1 root disk      1,  10 2010-11-14 13:25 ram10
brw-rw----  1 root disk      1,  11 2010-11-14 13:25 ram11
brw-rw----  1 root disk      1,  12 2010-11-14 13:25 ram12
brw-rw----  1 root disk      1,  13 2010-11-14 13:25 ram13
brw-rw----  1 root disk      1,  14 2010-11-14 13:25 ram14
brw-rw----  1 root disk      1,  15 2010-11-14 13:25 ram15
brw-rw----  1 root disk      1,   2 2010-11-14 13:25 ram2
brw-rw----  1 root disk      1,   3 2010-11-14 13:25 ram3
brw-rw----  1 root disk      1,   4 2010-11-14 13:25 ram4
brw-rw----  1 root disk      1,   5 2010-11-14 13:25 ram5
brw-rw----  1 root disk      1,   6 2010-11-14 13:25 ram6
brw-rw----  1 root disk      1,   7 2010-11-14 13:25 ram7
brw-rw----  1 root disk      1,   8 2010-11-14 13:25 ram8
brw-rw----  1 root disk      1,   9 2010-11-14 13:25 ram9
crw-rw-rw-  1 root root      1,   8 2010-11-14 13:25 random
crw-r--r--  1 root root     10,  62 2010-11-14 13:25 rfkill
lrwxrwxrwx  1 root root           4 2010-11-14 13:25 root -> sda5
lrwxrwxrwx  1 root root           4 2010-11-14 13:25 rtc -> rtc0
crw-------  1 root root    254,   0 2010-11-14 13:25 rtc0
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 scd0 -> sr0
brw-rw----  1 root disk      8,   0 2010-11-14 13:25 sda
brw-rw----  1 root disk      8,   1 2010-11-14 13:25 sda1
brw-rw----  1 root disk      8,   2 2010-11-14 13:25 sda2
brw-rw----  1 root disk      8,   5 2010-11-14 13:25 sda5
brw-rw----  1 root disk      8,   6 2010-11-14 13:25 sda6
crw-rw----  1 root cdrom    21,   0 2010-11-14 13:25 sg0
crw-rw----  1 root disk     21,   1 2010-11-14 13:25 sg1
drwxrwxrwt  2 root root         120 2010-11-14 13:27 shm
crw-------  1 root root     10, 231 2010-11-14 13:25 snapshot
drwxr-xr-x  3 root root         220 2010-11-14 13:25 snd
brw-rw----+ 1 root cdrom    11,   0 2010-11-14 13:25 sr0
lrwxrwxrwx  1 root root          15 2010-11-14 13:25 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2010-11-14 13:25 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2010-11-14 13:25 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root tty       5,   0 2010-11-14 13:26 tty
crw--w----  1 root root      4,   0 2010-11-14 13:25 tty0
crw-------  1 root root      4,   1 2010-11-14 13:25 tty1
crw--w----  1 root tty       4,  10 2010-11-14 13:25 tty10
crw--w----  1 root tty       4,  11 2010-11-14 13:25 tty11
crw--w----  1 root tty       4,  12 2010-11-14 13:25 tty12
crw--w----  1 root tty       4,  13 2010-11-14 13:25 tty13
crw--w----  1 root tty       4,  14 2010-11-14 13:25 tty14
crw--w----  1 root tty       4,  15 2010-11-14 13:25 tty15
crw--w----  1 root tty       4,  16 2010-11-14 13:25 tty16
crw--w----  1 root tty       4,  17 2010-11-14 13:25 tty17
crw--w----  1 root tty       4,  18 2010-11-14 13:25 tty18
crw--w----  1 root tty       4,  19 2010-11-14 13:25 tty19
crw-------  1 root root      4,   2 2010-11-14 13:25 tty2
crw--w----  1 root tty       4,  20 2010-11-14 13:25 tty20
crw--w----  1 root tty       4,  21 2010-11-14 13:25 tty21
crw--w----  1 root tty       4,  22 2010-11-14 13:25 tty22
crw--w----  1 root tty       4,  23 2010-11-14 13:25 tty23
crw--w----  1 root tty       4,  24 2010-11-14 13:25 tty24
crw--w----  1 root tty       4,  25 2010-11-14 13:25 tty25
crw--w----  1 root tty       4,  26 2010-11-14 13:25 tty26
crw--w----  1 root tty       4,  27 2010-11-14 13:25 tty27
crw--w----  1 root tty       4,  28 2010-11-14 13:25 tty28
crw--w----  1 root tty       4,  29 2010-11-14 13:25 tty29
crw-------  1 root root      4,   3 2010-11-14 13:25 tty3
crw--w----  1 root tty       4,  30 2010-11-14 13:25 tty30
crw--w----  1 root tty       4,  31 2010-11-14 13:25 tty31
crw--w----  1 root tty       4,  32 2010-11-14 13:25 tty32
crw--w----  1 root tty       4,  33 2010-11-14 13:25 tty33
crw--w----  1 root tty       4,  34 2010-11-14 13:25 tty34
crw--w----  1 root tty       4,  35 2010-11-14 13:25 tty35
crw--w----  1 root tty       4,  36 2010-11-14 13:25 tty36
crw--w----  1 root tty       4,  37 2010-11-14 13:25 tty37
crw--w----  1 root tty       4,  38 2010-11-14 13:25 tty38
crw--w----  1 root tty       4,  39 2010-11-14 13:25 tty39
crw-------  1 root root      4,   4 2010-11-14 13:25 tty4
crw--w----  1 root tty       4,  40 2010-11-14 13:25 tty40
crw--w----  1 root tty       4,  41 2010-11-14 13:25 tty41
crw--w----  1 root tty       4,  42 2010-11-14 13:25 tty42
crw--w----  1 root tty       4,  43 2010-11-14 13:25 tty43
crw--w----  1 root tty       4,  44 2010-11-14 13:25 tty44
crw--w----  1 root tty       4,  45 2010-11-14 13:25 tty45
crw--w----  1 root tty       4,  46 2010-11-14 13:25 tty46
crw--w----  1 root tty       4,  47 2010-11-14 13:25 tty47
crw--w----  1 root tty       4,  48 2010-11-14 13:25 tty48
crw--w----  1 root tty       4,  49 2010-11-14 13:25 tty49
crw-------  1 root root      4,   5 2010-11-14 13:25 tty5
crw--w----  1 root tty       4,  50 2010-11-14 13:25 tty50
crw--w----  1 root tty       4,  51 2010-11-14 13:25 tty51
crw--w----  1 root tty       4,  52 2010-11-14 13:25 tty52
crw--w----  1 root tty       4,  53 2010-11-14 13:25 tty53
crw--w----  1 root tty       4,  54 2010-11-14 13:25 tty54
crw--w----  1 root tty       4,  55 2010-11-14 13:25 tty55
crw--w----  1 root tty       4,  56 2010-11-14 13:25 tty56
crw--w----  1 root tty       4,  57 2010-11-14 13:25 tty57
crw--w----  1 root tty       4,  58 2010-11-14 13:25 tty58
crw--w----  1 root tty       4,  59 2010-11-14 13:25 tty59
crw-------  1 root root      4,   6 2010-11-14 13:25 tty6
crw--w----  1 root tty       4,  60 2010-11-14 13:25 tty60
crw--w----  1 root tty       4,  61 2010-11-14 13:25 tty61
crw--w----  1 root tty       4,  62 2010-11-14 13:25 tty62
crw--w----  1 root tty       4,  63 2010-11-14 13:25 tty63
crw--w----  1 root root      4,   7 2010-11-14 13:25 tty7
crw--w----  1 root tty       4,   8 2010-11-14 13:25 tty8
crw--w----  1 root tty       4,   9 2010-11-14 13:25 tty9
crw-rw----  1 root dialout   4,  64 2010-11-14 13:25 ttyS0
crw-rw----  1 root dialout   4,  65 2010-11-14 13:25 ttyS1
crw-rw----  1 root dialout   4,  66 2010-11-14 13:25 ttyS2
crw-rw----  1 root dialout   4,  67 2010-11-14 13:25 ttyS3
crw-r-----  1 root root     10, 223 2010-11-14 13:25 uinput
crw-rw-rw-  1 root root      1,   9 2010-11-14 13:25 urandom
crw-------  1 root root    252,   0 2010-11-14 13:25 usbmon0
crw-------  1 root root    252,   1 2010-11-14 13:25 usbmon1
crw-------  1 root root    252,   2 2010-11-14 13:25 usbmon2
crw-------  1 root root    252,   3 2010-11-14 13:25 usbmon3
crw-------  1 root root    252,   4 2010-11-14 13:25 usbmon4
crw-------  1 root root    252,   5 2010-11-14 13:25 usbmon5
crw-------  1 root root    252,   6 2010-11-14 13:25 usbmon6
crw-rw----  1 root tty       7,   0 2010-11-14 13:25 vcs
crw-rw----  1 root tty       7,   1 2010-11-14 13:25 vcs1
crw-rw----  1 root tty       7,   2 2010-11-14 13:25 vcs2
crw-rw----  1 root tty       7,   3 2010-11-14 13:25 vcs3
crw-rw----  1 root tty       7,   4 2010-11-14 13:25 vcs4
crw-rw----  1 root tty       7,   5 2010-11-14 13:25 vcs5
crw-rw----  1 root tty       7,   6 2010-11-14 13:25 vcs6
crw-rw----  1 root tty       7,   7 2010-11-14 13:25 vcs7
crw-rw----  1 root tty       7, 128 2010-11-14 13:25 vcsa
crw-rw----  1 root tty       7, 129 2010-11-14 13:25 vcsa1
crw-rw----  1 root tty       7, 130 2010-11-14 13:25 vcsa2
crw-rw----  1 root tty       7, 131 2010-11-14 13:25 vcsa3
crw-rw----  1 root tty       7, 132 2010-11-14 13:25 vcsa4
crw-rw----  1 root tty       7, 133 2010-11-14 13:25 vcsa5
crw-rw----  1 root tty       7, 134 2010-11-14 13:25 vcsa6
crw-rw----  1 root tty       7, 135 2010-11-14 13:25 vcsa7
crw-------  1 root root     10,  63 2010-11-14 13:25 vga_arbiter
crw-rw-rw-  1 root root      1,   5 2010-11-14 13:25 zero

```

There's the link there. 
lrwxrwxrwx  1 root root           3 2010-11-14 13:25 scd0 -> sr0

Lets try mounting sr0 directly instead.
```

root@Johnsky:/# mount -a /dev/sr0 /media/cdrom0
mount: /dev/sr0: unknown device

```

sr0 is still an unknown device.

I'm thinking when I reinstalled Ubuntu, it made some screwy links between devices. But I have no idea how to resolve this... and there's no point in my mind to adding the DVD-RW to /etc/fstab until I can actually mount it manually to know it mounts successfully.

Back when I installed Ubuntu 9.x on this machine, I never had any of these issues. It picked up the DVD-RW automatically, appended it to fstab during installation, and done, viola.
But 10.10 seems to be having some troubles my 9.x installation didn't.

---

### Post by johnsky on 2010-11-14
Update.

Ok, I have no idea what I did, (which by my recollection I didn't make any changes), but now it auto-mounts the drive when put a disk in the drive... and there's no fstab entries for the drive... I was under the impression... whatever.

However, I have to tell the drive to eject in order to load another CD/DVD into the drive. Otherwise it just shows the directory of the last CD/DVD in the drive.

At least it's better than nothing.
I suppose I can put up with it working this way until my next reinstall.

---

