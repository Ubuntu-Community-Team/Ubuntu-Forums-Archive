---
title: "mount: special device /dev/scd0 does not exist"
date: 2010-10-07
forum: General Help
---

### Post by iamjfarrell on 2010-10-07
This is what happens when I try to see what is on the CD in my CD drive. I don't understand. What do I need to do? It will not mount, but I can see it under "Computer"

---

### Post by lrgmmc on 2010-10-07
did you ```
ls -l /dev/
``` it may show up as sr0 at least thats how mine does

---

### Post by iamjfarrell on 2010-10-07
> **lrgmmc said:**
> did you ```
ls -l /dev/
``` it may show up as sr0 at least thats how mine does

```
ls -l /dev/
total 0
crw-rw----+ 1 root audio      14,  12 2010-10-05 23:05 adsp
crw-rw----+ 1 root audio      14,   4 2010-10-05 23:05 audio
drwxr-xr-x  2 root root           720 2010-10-05 19:05 block
drwxr-xr-x  2 root root            80 2010-10-05 19:05 bsg
drwxr-xr-x  3 root root            60 2010-10-05 19:05 bus
drwxr-xr-x  2 root root          3180 2010-10-07 11:05 char
crw-------  1 root root        5,   1 2010-10-05 23:05 console
lrwxrwxrwx  1 root root            11 2010-10-05 23:05 core -> /proc/kcore
crw-rw----  1 root root       10,  58 2010-10-05 23:05 cpu_dma_latency
drwxr-xr-x  6 root root           120 2010-10-05 19:05 disk
crw-rw----+ 1 root audio      14,   3 2010-10-05 23:05 dsp
crw-rw----  1 root root       10,  61 2010-10-05 23:05 ecryptfs
crw-rw----  1 root video      29,   0 2010-10-05 23:05 fb0
lrwxrwxrwx  1 root root            13 2010-10-05 23:05 fd -> /proc/self/fd
crw-rw-rw-  1 root root        1,   7 2010-10-05 23:05 full
crw-rw-rw-  1 root fuse       10, 229 2010-10-05 23:05 fuse
crw-rw----  1 root root       10, 228 2010-10-05 23:05 hpet
crw-rw----  1 root root       10, 183 2010-10-05 23:05 hwrng
drwxr-xr-x  4 root root           320 2010-10-05 23:05 input
crw-rw----  1 root root        1,  11 2010-10-05 23:05 kmsg
srw-rw-rw-  1 root root             0 2010-10-05 23:05 log
brw-rw----  1 root disk        7,   0 2010-10-05 23:05 loop0
brw-rw----  1 root disk        7,   1 2010-10-05 23:05 loop1
brw-rw----  1 root disk        7,   2 2010-10-05 23:05 loop2
brw-rw----  1 root disk        7,   3 2010-10-05 23:05 loop3
brw-rw----  1 root disk        7,   4 2010-10-05 23:05 loop4
brw-rw----  1 root disk        7,   5 2010-10-05 23:05 loop5
brw-rw----  1 root disk        7,   6 2010-10-05 23:05 loop6
brw-rw----  1 root disk        7,   7 2010-10-05 23:05 loop7
drwxr-xr-x  2 root root            60 2010-10-05 19:05 mapper
crw-rw----  1 root root       10, 227 2010-10-05 23:05 mcelog
crw-r-----  1 root kmem        1,   1 2010-10-05 23:05 mem
crw-rw----+ 1 root audio      14,   0 2010-10-05 23:05 mixer
drwxr-xr-x  2 root root            60 2010-09-09 18:09 net
crw-rw----  1 root root       10,  57 2010-10-05 23:05 network_latency
crw-rw----  1 root root       10,  56 2010-10-05 23:05 network_throughput
crw-rw-rw-  1 root root        1,   3 2010-10-05 23:05 null
crw-rw-rw-  1 root root      195,   0 2010-10-05 23:05 nvidia0
crw-rw-rw-  1 root root      195, 255 2010-10-05 23:05 nvidiactl
crw-rw----  1 root root        1,  12 2010-10-05 23:05 oldmem
drwxr-xr-x  2 root root            60 2010-10-05 19:05 pktcdvd
crw-r-----  1 root kmem        1,   4 2010-10-05 23:05 port
crw-------  1 root root      108,   0 2010-10-05 23:05 ppp
crw-rw----  1 root root       10,   1 2010-10-05 23:05 psaux
crw-rw-rw-  1 root tty         5,   2 2010-10-07 11:09 ptmx
drwxr-xr-x  2 root root             0 2009-10-16 02:01 pts
brw-rw----  1 root disk        1,   0 2010-10-05 23:05 ram0
brw-rw----  1 root disk        1,   1 2010-10-05 23:05 ram1
brw-rw----  1 root disk        1,  10 2010-10-05 23:05 ram10
brw-rw----  1 root disk        1,  11 2010-10-05 23:05 ram11
brw-rw----  1 root disk        1,  12 2010-10-05 23:05 ram12
brw-rw----  1 root disk        1,  13 2010-10-05 23:05 ram13
brw-rw----  1 root disk        1,  14 2010-10-05 23:05 ram14
brw-rw----  1 root disk        1,  15 2010-10-05 23:05 ram15
brw-rw----  1 root disk        1,   2 2010-10-05 23:05 ram2
brw-rw----  1 root disk        1,   3 2010-10-05 23:05 ram3
brw-rw----  1 root disk        1,   4 2010-10-05 23:05 ram4
brw-rw----  1 root disk        1,   5 2010-10-05 23:05 ram5
brw-rw----  1 root disk        1,   6 2010-10-05 23:05 ram6
brw-rw----  1 root disk        1,   7 2010-10-05 23:05 ram7
brw-rw----  1 root disk        1,   8 2010-10-05 23:05 ram8
brw-rw----  1 root disk        1,   9 2010-10-05 23:05 ram9
crw-rw-rw-  1 root root        1,   8 2010-10-05 23:05 random
crw-rw-r--+ 1 root root       10,  62 2010-10-05 23:05 rfkill
lrwxrwxrwx  1 root root             4 2010-10-05 23:05 root -> sda6
lrwxrwxrwx  1 root root             4 2010-10-05 23:05 rtc -> rtc0
crw-rw----  1 root root      254,   0 2010-10-05 23:05 rtc0
brw-rw----  1 root disk        8,   0 2010-10-05 23:05 sda
brw-rw----  1 root disk        8,   1 2010-10-05 23:05 sda1
brw-rw----  1 root disk        8,   2 2010-10-05 23:05 sda2
brw-rw----  1 root disk        8,   3 2010-10-05 23:05 sda3
brw-rw----  1 root disk        8,   4 2010-10-05 23:05 sda4
brw-rw----  1 root disk        8,   5 2010-10-05 23:05 sda5
brw-rw----  1 root disk        8,   6 2010-10-05 23:05 sda6
brw-rw----  1 root disk        8,   7 2010-10-05 23:05 sda7
brw-rw----  1 root disk        8,  16 2010-10-05 23:05 sdb
brw-rw----  1 root disk        8,  17 2010-10-05 23:05 sdb1
crw-rw----+ 1 root audio      14,   1 2010-10-05 23:05 sequencer
crw-rw----+ 1 root audio      14,   8 2010-10-05 23:05 sequencer2
crw-rw----  1 root disk       21,   0 2010-10-05 23:05 sg0
crw-rw----  1 root disk       21,   1 2010-10-05 23:05 sg1
drwxrwxrwt  2 root root           260 2010-10-07 11:04 shm
crw-rw----  1 root root       10, 231 2010-10-05 23:05 snapshot
drwxr-xr-x  3 root root           200 2010-10-05 23:05 snd
lrwxrwxrwx  1 root root            24 2010-10-05 23:05 sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx  1 root root            15 2010-10-05 23:05 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root            15 2010-10-05 23:05 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root            15 2010-10-05 23:05 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root tty         5,   0 2010-10-07 10:56 tty
crw--w----  1 root root        4,   0 2010-10-05 23:05 tty0
crw-------  1 root root        4,   1 2010-10-05 23:05 tty1
crw--w----  1 root tty         4,  10 2010-10-05 23:05 tty10
crw--w----  1 root tty         4,  11 2010-10-05 23:05 tty11
crw--w----  1 root tty         4,  12 2010-10-05 23:05 tty12
crw--w----  1 root tty         4,  13 2010-10-05 23:05 tty13
crw--w----  1 root tty         4,  14 2010-10-05 23:05 tty14
crw--w----  1 root tty         4,  15 2010-10-05 23:05 tty15
crw--w----  1 root tty         4,  16 2010-10-05 23:05 tty16
crw--w----  1 root tty         4,  17 2010-10-05 23:05 tty17
crw--w----  1 root tty         4,  18 2010-10-05 23:05 tty18
crw--w----  1 root tty         4,  19 2010-10-05 23:05 tty19
crw-------  1 root root        4,   2 2010-10-05 23:05 tty2
crw--w----  1 root tty         4,  20 2010-10-05 23:05 tty20
crw--w----  1 root tty         4,  21 2010-10-05 23:05 tty21
crw--w----  1 root tty         4,  22 2010-10-05 23:05 tty22
crw--w----  1 root tty         4,  23 2010-10-05 23:05 tty23
crw--w----  1 root tty         4,  24 2010-10-05 23:05 tty24
crw--w----  1 root tty         4,  25 2010-10-05 23:05 tty25
crw--w----  1 root tty         4,  26 2010-10-05 23:05 tty26
crw--w----  1 root tty         4,  27 2010-10-05 23:05 tty27
crw--w----  1 root tty         4,  28 2010-10-05 23:05 tty28
crw--w----  1 root tty         4,  29 2010-10-05 23:05 tty29
crw-------  1 root root        4,   3 2010-10-05 23:05 tty3
crw--w----  1 root tty         4,  30 2010-10-05 23:05 tty30
crw--w----  1 root tty         4,  31 2010-10-05 23:05 tty31
crw--w----  1 root tty         4,  32 2010-10-05 23:05 tty32
crw--w----  1 root tty         4,  33 2010-10-05 23:05 tty33
crw--w----  1 root tty         4,  34 2010-10-05 23:05 tty34
crw--w----  1 root tty         4,  35 2010-10-05 23:05 tty35
crw--w----  1 root tty         4,  36 2010-10-05 23:05 tty36
crw--w----  1 root tty         4,  37 2010-10-05 23:05 tty37
crw--w----  1 root tty         4,  38 2010-10-05 23:05 tty38
crw--w----  1 root tty         4,  39 2010-10-05 23:05 tty39
crw-------  1 root root        4,   4 2010-10-05 23:05 tty4
crw--w----  1 root tty         4,  40 2010-10-05 23:05 tty40
crw--w----  1 root tty         4,  41 2010-10-05 23:05 tty41
crw--w----  1 root tty         4,  42 2010-10-05 23:05 tty42
crw--w----  1 root tty         4,  43 2010-10-05 23:05 tty43
crw--w----  1 root tty         4,  44 2010-10-05 23:05 tty44
crw--w----  1 root tty         4,  45 2010-10-05 23:05 tty45
crw--w----  1 root tty         4,  46 2010-10-05 23:05 tty46
crw--w----  1 root tty         4,  47 2010-10-05 23:05 tty47
crw--w----  1 root tty         4,  48 2010-10-05 23:05 tty48
crw--w----  1 root tty         4,  49 2010-10-05 23:05 tty49
crw-------  1 root root        4,   5 2010-10-05 23:05 tty5
crw--w----  1 root tty         4,  50 2010-10-05 23:05 tty50
crw--w----  1 root tty         4,  51 2010-10-05 23:05 tty51
crw--w----  1 root tty         4,  52 2010-10-05 23:05 tty52
crw--w----  1 root tty         4,  53 2010-10-05 23:05 tty53
crw--w----  1 root tty         4,  54 2010-10-05 23:05 tty54
crw--w----  1 root tty         4,  55 2010-10-05 23:05 tty55
crw--w----  1 root tty         4,  56 2010-10-05 23:05 tty56
crw--w----  1 root tty         4,  57 2010-10-05 23:05 tty57
crw--w----  1 root tty         4,  58 2010-10-05 23:05 tty58
crw--w----  1 root tty         4,  59 2010-10-05 23:05 tty59
crw-------  1 root root        4,   6 2010-10-05 23:05 tty6
crw--w----  1 root tty         4,  60 2010-10-05 23:05 tty60
crw--w----  1 root tty         4,  61 2010-10-05 23:05 tty61
crw--w----  1 root tty         4,  62 2010-10-05 23:05 tty62
crw--w----  1 root tty         4,  63 2010-10-05 23:05 tty63
crw--w----  1 root root        4,   7 2010-10-05 23:05 tty7
crw--w----  1 root tty         4,   8 2010-10-05 23:05 tty8
crw--w----  1 root tty         4,   9 2010-10-05 23:05 tty9
crw-rw----  1 root dialout     4,  64 2010-10-05 23:05 ttyS0
crw-rw----  1 root dialout     4,  65 2010-10-05 23:05 ttyS1
crw-rw----  1 root dialout     4,  66 2010-10-05 23:05 ttyS2
crw-rw----  1 root dialout     4,  67 2010-10-05 23:05 ttyS3
crw-rw-rw-  1 root root        1,   9 2010-10-05 23:05 urandom
crw-rw----  1 root root      252,   0 2010-10-05 23:05 usbmon0
crw-rw----  1 root root      252,   1 2010-10-05 23:05 usbmon1
crw-rw----  1 root root      252,   2 2010-10-05 23:05 usbmon2
crw-rw----  1 root root      252,   3 2010-10-05 23:05 usbmon3
crw-rw----  1 root root      252,   4 2010-10-05 23:05 usbmon4
drwxr-xr-x  4 root root            80 2010-10-05 23:05 v4l
crw-------  1 root vboxusers  10,  55 2010-10-05 23:05 vboxdrv
crw-rw----  1 root root       10,  54 2010-10-05 23:05 vboxnetctl
crw-rw----  1 root tty         7,   0 2010-10-05 23:05 vcs
crw-rw----  1 root tty         7,   1 2010-10-05 23:05 vcs1
crw-rw----  1 root tty         7,   2 2010-10-05 23:05 vcs2
crw-rw----  1 root tty         7,   3 2010-10-05 23:05 vcs3
crw-rw----  1 root tty         7,   4 2010-10-05 23:05 vcs4
crw-rw----  1 root tty         7,   5 2010-10-05 23:05 vcs5
crw-rw----  1 root tty         7,   6 2010-10-05 23:05 vcs6
crw-rw----  1 root tty         7,   7 2010-10-05 23:05 vcs7
crw-rw----  1 root tty         7, 128 2010-10-05 23:05 vcsa
crw-rw----  1 root tty         7, 129 2010-10-05 23:05 vcsa1
crw-rw----  1 root tty         7, 130 2010-10-05 23:05 vcsa2
crw-rw----  1 root tty         7, 131 2010-10-05 23:05 vcsa3
crw-rw----  1 root tty         7, 132 2010-10-05 23:05 vcsa4
crw-rw----  1 root tty         7, 133 2010-10-05 23:05 vcsa5
crw-rw----  1 root tty         7, 134 2010-10-05 23:05 vcsa6
crw-rw----  1 root tty         7, 135 2010-10-05 23:05 vcsa7
crw-rw----  1 root root       10,  63 2010-10-05 23:05 vga_arbiter
crw-rw----+ 1 root video      81,   0 2010-10-05 23:05 video0
crw-rw-rw-  1 root root        1,   5 2010-10-05 23:05 zero
```

That is the output I got. I couldn't find where my CD rom would be.

---

### Post by psusi on 2010-10-07
Yep, you don't appear to have a ( functioning ) cd.

---

