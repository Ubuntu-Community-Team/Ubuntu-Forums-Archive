---
title: "Partition won't mount after reboot"
date: 2010-08-17
forum: General Help
---

### Post by guitarMan666 on 2010-08-17
After following a guide on ghacks ([http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4](http://www.ghacks.net/2010/08/11/convert-ext23-to-ext4)) I am now left with a damn odd problem.  Following the guide worked perfectly, for a while, until I got to Step 6.

At Step 6 it refers to running grub-install with some switches. It looked like this for my machine:

```

root@Microknoppix:~# mount /dev/sda3 /mnt
root@Microknoppix:~# grub-install /dev/sda/ --root-directory=/mnt --rechcheck
File /mnt/boot/grub/stage1 not read correctly.

```

The wording on that error message may not be exact but it does convey the meaning. I tried this a few times, nothing bad happened. I then rebooted thinking that perhaps it was benign or even a warning. Ubuntu booted properly with no errors but booted slowly. I went into the disk utility and ran some self tests which didn't yield anything, although the "disk has some bad sectors." 190 according to Disk Utility. I then learned that the file system was mounted read only while wasting time playing tetris in Emacs it said "could not lock score file. read-only file system." I thought this was an Emacs issue so I ran:
```

user@avandar:~$ touch txt.txt
Error: Could not touch txt.txt read-only file system.

```

I then, probably my biggest mistake, attempted to reboot. It now just sits where it should start grub and say "Press Esc to display menu" doing absolutely nothing (it seems to reboot after a short time). I then successfully boot into Knoppix (while doing so it sits for a LONG time when it is "Searching for Knoppix in sda3). Attempting to mount the partition NOW yields:

```

knoppix@Microknoppix:/mnt$ sudo mount -t ext4 /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I have also tried: ```
sudo mount -t ext4 /dev/sda3 /mnt -o error=continue
``` and ```
 sudo mount -t ext4 /dev/sda3 /mnt -o bs=8391
``` as suggested on the Linux Forums.

In all cases dmesg yeilds:
```

$ dmesg | tail
[ 1771.113877] ata1: EH complete
[ 1773.312062] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 1773.312065] ata1.00: irq_stat 0x40000001
[ 1773.312068] ata1.00: failed command: READ DMA
[ 1773.312074] ata1.00: cmd c8/00:02:1a:4c:a1/00:00:00:00:00/e0 tag 0 dma 1024 in
[ 1773.312075]          res 51/40:00:1a:4c:a1/00:00:00:00:00/00 Emask 0x9 (media error)
[ 1773.312078] ata1.00: status: { DRDY ERR }
[ 1773.312080] ata1.00: error: { UNC }
[ 1773.446103] ata1.00: configured for UDMA/133
[ 1773.446111] ata1: EH complete
```

Some of what I see in there leads me to believe there is a hardware issue, but I have no clue as the other partition (sda1) mounts just fine (but can't be booted because of GRUB not loading. Any ideas just to get this puppy mounted would be greatly appreciated, I've slipped out of my depth.

---

