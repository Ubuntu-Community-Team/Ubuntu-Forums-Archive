---
title: "Default Permissions"
date: 2009-11-18
forum: General Help
---

### Post by frediokl on 2009-11-18
I have a vps that is running ubuntu and I did something silly!
 
chown -R wishlist / instead of chown -R wishlist .
 
I stopped it as soon as i realised but....
 
So I now have a /dev and a /var directories with everything owned by wishlist!
 
could someone send me an ls -l of these directories for a clean install so I can set them back to the correct owner.

---

### Post by frediokl on 2009-11-18
No one want to help :confused: Is there another way to set files back to their default owners. I was told rpc has something

---

### Post by emigrant on 2009-11-18
you mean you changed root owned directories to wishlist?
so why not giving 
```

sudo chown -R root /var 

```and
```

sudo chown -R root /dev

```

---

### Post by gdonwallace on 2009-11-18
Here is what I have in /var:

drwxr-xr-x  2 root root  4096 2009-11-14 08:04 backups
drwxr-xr-x 20 root root  4096 2009-11-09 19:41 cache
drwxrwxrwt  2 root root  4096 2009-11-11 08:06 crash
drwxr-xr-x  2 root root  4096 2009-04-20 09:07 games
drwxr-xr-x 61 root root  4096 2009-11-12 14:19 lib
drwxrwsr-x  2 root staff 4096 2009-04-13 04:33 local
drwxrwxrwt  2 root root    40 2009-11-18 10:37 lock
drwxr-xr-x 14 root root  4096 2009-11-18 10:36 log
drwxrwsr-x  2 root mail  4096 2009-04-20 08:59 mail
drwxr-xr-x  2 root root  4096 2009-04-20 08:59 opt
drwxr-xr-x 15 root root   580 2009-11-18 10:07 run
drwxr-xr-x  6 root root  4096 2009-10-23 19:33 spool
drwxrwxrwt  2 root root  4096 2009-11-18 12:47 tmp


And this is what is in /dev:
crw-rw----+ 1 root audio    14,  12 2009-11-18 10:06 adsp
crw-------  1 root video    10, 175 2009-11-18 10:06 agpgart
crw-rw----+ 1 root audio    14,   4 2009-11-18 10:06 audio
crw-rw----  1 root root     10,  59 2009-11-18 10:06 binder
drwxr-xr-x  2 root root         640 2009-11-18 10:06 block
drwxr-xr-x  3 root root          60 2009-11-18 10:06 bus
lrwxrwxrwx  1 root root           3 2009-11-18 10:06 cdrom -> sr0
lrwxrwxrwx  1 root root           3 2009-11-18 10:06 cdrw -> sr0
drwxr-xr-x  2 root root        3200 2009-11-18 10:06 char
crw-------  1 root root      5,   1 2009-11-18 10:36 console
lrwxrwxrwx  1 root root          11 2009-11-18 10:06 core -> /proc/kcore
crw-rw----  1 root root     10,  58 2009-11-18 10:06 cpu_dma_latency
drwxr-xr-x  5 root root         100 2009-11-18 10:06 disk
drwxr-xr-x  2 root root          80 2009-11-18 10:06 dri
crw-rw----+ 1 root audio    14,   3 2009-11-18 10:06 dsp
lrwxrwxrwx  1 root root           3 2009-11-18 10:06 dvd -> sr0
crw-rw----  1 root root     10,  62 2009-11-18 10:06 ecryptfs
crw-rw----  1 root video    29,   0 2009-11-18 10:06 fb0
lrwxrwxrwx  1 root root          13 2009-11-18 10:06 fd -> /proc/self/fd
crw-rw-rw-  1 root root      1,   7 2009-11-18 10:06 full
crw-rw-rw-  1 root fuse     10, 229 2009-11-18 10:06 fuse
crw-rw----  1 root root     10, 228 2009-11-18 10:06 hpet
drwxr-xr-x  3 root root         320 2009-11-18 10:06 input
crw-rw----  1 root root      1,  11 2009-11-18 10:06 kmsg
srw-rw-rw-  1 root root           0 2009-11-18 10:06 log
brw-rw----  1 root disk      7,   0 2009-11-18 10:06 loop0
brw-rw----  1 root disk      7,   1 2009-11-18 10:06 loop1
brw-rw----  1 root disk      7,   2 2009-11-18 10:06 loop2
brw-rw----  1 root disk      7,   3 2009-11-18 10:06 loop3
brw-rw----  1 root disk      7,   4 2009-11-18 10:06 loop4
brw-rw----  1 root disk      7,   5 2009-11-18 10:06 loop5
brw-rw----  1 root disk      7,   6 2009-11-18 10:06 loop6
brw-rw----  1 root disk      7,   7 2009-11-18 10:06 loop7
crw-rw----  1 root lp        6,   0 2009-11-18 10:06 lp0
drwxr-xr-x  2 root root          60 2009-11-18 10:06 mapper
crw-rw----  1 root root     10, 227 2009-11-18 10:06 mcelog
crw-r-----  1 root kmem      1,   1 2009-11-18 10:06 mem
crw-rw----+ 1 root audio    14,   0 2009-11-18 10:06 mixer
drwxr-xr-x  2 root root          60 2009-11-18 10:06 net
crw-rw----  1 root root     10,  57 2009-11-18 10:06 network_latency
crw-rw----  1 root root     10,  56 2009-11-18 10:06 network_throughput
crw-rw-rw-  1 root root      1,   3 2009-11-18 10:06 null
crw-rw----  1 root root      1,  12 2009-11-18 10:06 oldmem
crw-rw----  1 root lp       99,   0 2009-11-18 10:06 parport0
drwxr-xr-x  2 root root          60 2009-11-18 10:06 pktcdvd
crw-r-----  1 root kmem      1,   4 2009-11-18 10:06 port
crw-------  1 root root    108,   0 2009-11-18 10:06 ppp
crw-rw----  1 root root     10,   1 2009-11-18 10:06 psaux
crw-rw-rw-  1 root tty       5,   2 2009-11-18 12:49 ptmx
drwxr-xr-x  2 root root           0 2009-11-18 10:06 pts
brw-rw----  1 root disk      1,   0 2009-11-18 10:06 ram0
brw-rw----  1 root disk      1,   1 2009-11-18 10:06 ram1
brw-rw----  1 root disk      1,  10 2009-11-18 10:06 ram10
brw-rw----  1 root disk      1,  11 2009-11-18 10:06 ram11
brw-rw----  1 root disk      1,  12 2009-11-18 10:06 ram12
brw-rw----  1 root disk      1,  13 2009-11-18 10:06 ram13
brw-rw----  1 root disk      1,  14 2009-11-18 10:06 ram14
brw-rw----  1 root disk      1,  15 2009-11-18 10:06 ram15
brw-rw----  1 root disk      1,   2 2009-11-18 10:06 ram2
brw-rw----  1 root disk      1,   3 2009-11-18 10:06 ram3
brw-rw----  1 root disk      1,   4 2009-11-18 10:06 ram4
brw-rw----  1 root disk      1,   5 2009-11-18 10:06 ram5
brw-rw----  1 root disk      1,   6 2009-11-18 10:06 ram6
brw-rw----  1 root disk      1,   7 2009-11-18 10:06 ram7
brw-rw----  1 root disk      1,   8 2009-11-18 10:06 ram8
brw-rw----  1 root disk      1,   9 2009-11-18 10:06 ram9
crw-rw-rw-  1 root root      1,   8 2009-11-18 10:06 random
crw-rw-r--+ 1 root root     10,  63 2009-11-18 10:06 rfkill
lrwxrwxrwx  1 root root           4 2009-11-18 10:06 rtc -> rtc0
crw-rw----  1 root root    254,   0 2009-11-18 10:06 rtc0
lrwxrwxrwx  1 root root           3 2009-11-18 10:06 scd0 -> sr0
brw-rw----  1 root disk      8,   0 2009-11-18 10:06 sda
brw-rw----  1 root disk      8,   1 2009-11-18 10:06 sda1
brw-rw----  1 root disk      8,   2 2009-11-18 10:06 sda2
brw-rw----  1 root disk      8,   5 2009-11-18 10:06 sda5
brw-rw----  1 root disk      8,   6 2009-11-18 10:06 sda6
crw-rw----+ 1 root audio    14,   1 2009-11-18 10:06 sequencer
crw-rw----+ 1 root audio    14,   8 2009-11-18 10:06 sequencer2
crw-rw----  1 root disk     21,   0 2009-11-18 10:06 sg0
crw-rw----  1 root cdrom    21,   1 2009-11-18 10:06 sg1
drwxrwxrwt  2 root root         140 2009-11-18 12:47 shm
crw-rw----  1 root root     10, 231 2009-11-18 10:06 snapshot
drwxr-xr-x  3 root root         240 2009-11-18 10:06 snd
lrwxrwxrwx  1 root root          24 2009-11-18 10:06 sndstat -> /proc/asound/oss/sndstat
brw-rw----+ 1 root cdrom    11,   0 2009-11-18 10:06 sr0
lrwxrwxrwx  1 root root          15 2009-11-18 10:06 stderr -> /proc/self/fd/2
lrwxrwxrwx  1 root root          15 2009-11-18 10:06 stdin -> /proc/self/fd/0
lrwxrwxrwx  1 root root          15 2009-11-18 10:06 stdout -> /proc/self/fd/1
crw-rw-rw-  1 root tty       5,   0 2009-11-18 10:06 tty
crw--w----  1 root root      4,   0 2009-11-18 10:06 tty0
crw-------  1 root root      4,   1 2009-11-18 10:06 tty1
crw--w----  1 root tty       4,  10 2009-11-18 10:06 tty10
crw--w----  1 root tty       4,  11 2009-11-18 10:06 tty11
crw--w----  1 root tty       4,  12 2009-11-18 10:06 tty12
crw--w----  1 root tty       4,  13 2009-11-18 10:06 tty13
crw--w----  1 root tty       4,  14 2009-11-18 10:06 tty14
crw--w----  1 root tty       4,  15 2009-11-18 10:06 tty15
crw--w----  1 root tty       4,  16 2009-11-18 10:06 tty16
crw--w----  1 root tty       4,  17 2009-11-18 10:06 tty17
crw--w----  1 root tty       4,  18 2009-11-18 10:06 tty18
crw--w----  1 root tty       4,  19 2009-11-18 10:06 tty19
crw-------  1 root root      4,   2 2009-11-18 10:06 tty2
crw--w----  1 root tty       4,  20 2009-11-18 10:06 tty20
crw--w----  1 root tty       4,  21 2009-11-18 10:06 tty21
crw--w----  1 root tty       4,  22 2009-11-18 10:06 tty22
crw--w----  1 root tty       4,  23 2009-11-18 10:06 tty23
crw--w----  1 root tty       4,  24 2009-11-18 10:06 tty24
crw--w----  1 root tty       4,  25 2009-11-18 10:06 tty25
crw--w----  1 root tty       4,  26 2009-11-18 10:06 tty26
crw--w----  1 root tty       4,  27 2009-11-18 10:06 tty27
crw--w----  1 root tty       4,  28 2009-11-18 10:06 tty28
crw--w----  1 root tty       4,  29 2009-11-18 10:06 tty29
crw-------  1 root root      4,   3 2009-11-18 10:06 tty3
crw--w----  1 root tty       4,  30 2009-11-18 10:06 tty30
crw--w----  1 root tty       4,  31 2009-11-18 10:06 tty31
crw--w----  1 root tty       4,  32 2009-11-18 10:06 tty32
crw--w----  1 root tty       4,  33 2009-11-18 10:06 tty33
crw--w----  1 root tty       4,  34 2009-11-18 10:06 tty34
crw--w----  1 root tty       4,  35 2009-11-18 10:06 tty35
crw--w----  1 root tty       4,  36 2009-11-18 10:06 tty36
crw--w----  1 root tty       4,  37 2009-11-18 10:06 tty37
crw--w----  1 root tty       4,  38 2009-11-18 10:06 tty38
crw--w----  1 root tty       4,  39 2009-11-18 10:06 tty39
crw-------  1 root root      4,   4 2009-11-18 10:06 tty4
crw--w----  1 root tty       4,  40 2009-11-18 10:06 tty40
crw--w----  1 root tty       4,  41 2009-11-18 10:06 tty41
crw--w----  1 root tty       4,  42 2009-11-18 10:06 tty42
crw--w----  1 root tty       4,  43 2009-11-18 10:06 tty43
crw--w----  1 root tty       4,  44 2009-11-18 10:06 tty44
crw--w----  1 root tty       4,  45 2009-11-18 10:06 tty45
crw--w----  1 root tty       4,  46 2009-11-18 10:06 tty46
crw--w----  1 root tty       4,  47 2009-11-18 10:06 tty47
crw--w----  1 root tty       4,  48 2009-11-18 10:06 tty48
crw--w----  1 root tty       4,  49 2009-11-18 10:06 tty49
crw-------  1 root root      4,   5 2009-11-18 10:06 tty5
crw--w----  1 root tty       4,  50 2009-11-18 10:06 tty50
crw--w----  1 root tty       4,  51 2009-11-18 10:06 tty51
crw--w----  1 root tty       4,  52 2009-11-18 10:06 tty52
crw--w----  1 root tty       4,  53 2009-11-18 10:06 tty53
crw--w----  1 root tty       4,  54 2009-11-18 10:06 tty54
crw--w----  1 root tty       4,  55 2009-11-18 10:06 tty55
crw--w----  1 root tty       4,  56 2009-11-18 10:06 tty56
crw--w----  1 root tty       4,  57 2009-11-18 10:06 tty57
crw--w----  1 root tty       4,  58 2009-11-18 10:06 tty58
crw--w----  1 root tty       4,  59 2009-11-18 10:06 tty59
crw-------  1 root root      4,   6 2009-11-18 10:06 tty6
crw--w----  1 root tty       4,  60 2009-11-18 10:06 tty60
crw--w----  1 root tty       4,  61 2009-11-18 10:06 tty61
crw--w----  1 root tty       4,  62 2009-11-18 10:06 tty62
crw--w----  1 root tty       4,  63 2009-11-18 10:06 tty63
crw--w----  1 root root      4,   7 2009-11-18 10:06 tty7
crw--w----  1 root tty       4,   8 2009-11-18 10:06 tty8
crw--w----  1 root tty       4,   9 2009-11-18 10:06 tty9
crw-rw----  1 root dialout   4,  64 2009-11-18 10:06 ttyS0
crw-rw----  1 root dialout   4,  65 2009-11-18 10:06 ttyS1
crw-rw----  1 root dialout   4,  66 2009-11-18 10:06 ttyS2
crw-rw----  1 root dialout   4,  67 2009-11-18 10:06 ttyS3
crw-rw-rw-  1 root root      1,   9 2009-11-18 10:06 urandom
crw-rw----  1 root root    253,   0 2009-11-18 10:06 usbmon0
crw-rw----  1 root root    253,   1 2009-11-18 10:06 usbmon1
crw-rw----  1 root root    253,   2 2009-11-18 10:06 usbmon2
crw-rw----  1 root root    253,   3 2009-11-18 10:06 usbmon3
crw-rw----  1 root root    253,   4 2009-11-18 10:06 usbmon4
crw-rw----  1 root root    253,   5 2009-11-18 10:06 usbmon5
crw-rw----  1 root tty       7,   0 2009-11-18 10:06 vcs
crw-rw----  1 root tty       7,   1 2009-11-18 10:06 vcs1
crw-rw----  1 root tty       7,   2 2009-11-18 10:06 vcs2
crw-rw----  1 root tty       7,   3 2009-11-18 10:06 vcs3
crw-rw----  1 root tty       7,   4 2009-11-18 10:06 vcs4
crw-rw----  1 root tty       7,   5 2009-11-18 10:06 vcs5
crw-rw----  1 root tty       7,   6 2009-11-18 10:06 vcs6
crw-rw----  1 root tty       7,   7 2009-11-18 10:06 vcs7
crw-rw----  1 root tty       7, 128 2009-11-18 10:06 vcsa
crw-rw----  1 root tty       7, 129 2009-11-18 10:06 vcsa1
crw-rw----  1 root tty       7, 130 2009-11-18 10:06 vcsa2
crw-rw----  1 root tty       7, 131 2009-11-18 10:06 vcsa3
crw-rw----  1 root tty       7, 132 2009-11-18 10:06 vcsa4
crw-rw----  1 root tty       7, 133 2009-11-18 10:06 vcsa5
crw-rw----  1 root tty       7, 134 2009-11-18 10:06 vcsa6
crw-rw----  1 root tty       7, 135 2009-11-18 10:06 vcsa7
crw-rw-rw-  1 root root      1,   5 2009-11-18 10:06 zero


Hope this helps

---

### Post by frediokl on 2009-11-18
@emigrant was not sure they were all owned by root so did not want to do that!
 
Thanks gd, looks like all top level are all root owned so emigrant's solution looks good, not sure about the -R bit though. Eg under var/lib i have mysql which i know should be owned by mysql. Just going through them now, will post any I am not sure about.

---

### Post by doas777 on 2009-11-18
it will be fine to just change /dev back. I'm a little worried about /var though. there are some entries in /var/run that are not owned by root, including dbus. same with /var/lib etc.

---

### Post by frediokl on 2009-11-18
I'm up to var/log I assume I should be ok to delete all the log files as new ones will be created with the right owners, right?

---

### Post by doas777 on 2009-11-18
> **frediokl said:**
> I'm up to var/log I assume I should be ok to delete all the log files as new ones will be created with the right owners, right?

I would have to assume, but I've never tried it TBH.

---

### Post by Giblet5 on 2009-11-18
There's no way of knowing what all got changed, and correcting the permissions on every file, folder, device, named pipe, unix-domain socket, and link is not physically possible before Sol novas.

I would back up the home folder using tar, then reinstall.

---

