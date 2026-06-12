---
title: "Kubuntu really slow"
date: 2006-03-01
forum: General Help
---

### Post by johnFI on 2006-03-01
Hi,
I just installed Kubuntu,but kde is running really slow!
Here's what top command shows:
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
29378 root      15   0 98244  14m 2512 S  2.7  1.4   0:35.49 Xorg
29563 john      15   0 29468  15m  13m S  2.0  1.6   0:00.87 konsole
29531 john      15   0 94084  31m  17m S  1.3  3.1   0:42.87 firefox-bin
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.10 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.20 events/0
    4 root      12  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   97 root      10  -5     0    0    0 S  0.0  0.0   0:00.61 kblockd/0
  126 root      15   0     0    0    0 S  0.0  0.0   0:02.05 pdflush
  127 root      15   0     0    0    0 S  0.0  0.0   0:00.50 pdflush
  129 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  128 root      15   0     0    0    0 S  0.0  0.0   0:04.19 kswapd0
  714 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1892 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1895 root      25   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0

```
And I'm not running anything special:Firefox,xmms,kopete,and if I try to view eg. "Configure Desktop" at the same time(eg. to change a BG) it takes about 5-15secs to show up and some times it crashes!
Also I tried to copy data from dvd to hd,while xmms was playing,and again kde became very slow.
My specs are,1GB ram,2.6ghz P4,512 swap,S-ATA hd,Geforce 4 mx440 vga.
Any suggestions?

ps.This behavior is after a fresh install

---

### Post by gingermark on 2006-03-01
It shouldn't be that slow. I'd suggest installing and booting off the 686 kernel and seeing if that improves matters.

---

### Post by johnFI on 2006-03-01
I just tried that,but the results were the same..
It's like somebody's trying to work with WinXp on a P2 300Mhz and 128mb ram..

---

### Post by johnFI on 2006-03-01
Here's "top" output,while I was copying data from dvd->hd,playing some mp3s with xmms,surfing with firefox(2 tabs),and having Kopete on tray:
```
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 8297 john      15   0 47760 8212 5184 S 41.4  0.8   3:25.55 xmms
 7671 root      16   0 99.7m  17m 3016 R 12.6  1.8   1:50.80 Xorg
 8371 root      18   0  2948  608  452 R 12.0  0.1   1:42.03 cp
 8212 john      15   0 30604  17m  13m S  5.8  1.7   0:30.16 kmix
 8412 john      15   0 30860  16m  13m S  4.8  1.6   0:02.28 konsole
 8171 john      15   0 39704  16m  13m S  3.9  1.6   0:14.29 kded
 8192 john      15   0 35580  17m  13m S  3.6  1.7   0:20.43 knotify
  128 root      16   0     0    0    0 S  2.9  0.0   0:21.74 kswapd0
 7883 john      15   0  2804 1524  888 S  2.6  0.1   0:20.74 gam_server
 8179 john      15   0 13516 7704 5360 S  1.3  0.7   0:07.44 artsd
 8209 john      15   0 27732  13m  11m S  1.0  1.4   0:08.27 klipper
   97 root      10  -5     0    0    0 S  0.6  0.0   0:00.62 kblockd/0
    3 root      10  -5     0    0    0 S  0.3  0.0   0:02.27 events/0
 8190 john      15   0 29052  15m  12m S  0.3  1.5   0:05.53 kwin
    1 root      16   0  1564  532  460 S  0.0  0.1   0:01.16 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelp
```

---

### Post by GeneralZod on 2006-03-01
I have no idea what could be causing this - it's definitely not normal.

As for slowing copying from a DVD drive - is DMA enabled on the drive?

Also, check whether messages are being poured in /var/log/messages and ~/.xsession-errors

Edit:

Wait a minute - are you trying to use composite? Check your /etc/X11/xorg.conf, and see if:

```

Option "Composite" "Enable"

```

is in it.  If so, comment it out, save your work, and restart X.

---

### Post by johnFI on 2006-03-01
There is no composite option in xorg.conf and I didn't find anything weird in /var/log/messages,should I look for something specific?

---

