---
title: "Ubuntu 10.10 freezes on startup"
date: 2011-04-15
forum: General Help
---

### Post by leapinglangoor on 2011-04-15
It started after a crash due to a blackout. Ubuntu freezes on startup.
Irritating workaround: I have to use tty1 to restart X.
Even after that the system is slow(like theres something really wrong with the graphics) and it usually fixes a little if I run compiz.

Edit: This problem occurred before when I updated gdm to the latest version. 
I had to reinstall ubuntu because of that.

I might have found the root of the problem in dmesg output(whole thing is attached):
```
[   16.697020] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:05.0 on minor 0
[   17.543826] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   17.796195] tg3 0000:10:00.0: eth0: Link is up at 100 Mbps, full duplex
[   17.796200] tg3 0000:10:00.0: eth0: Flow control is off for TX and off for RX
[   17.796457] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   19.920492] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   28.272037] eth0: no IPv6 routers present
[   29.484110] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   29.484226] ata1.00: ST_FIRST: !(DRQ|ERR|DF)
[   29.484298] sr 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
[   29.484313] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[   29.484315]          res 50/40:41:40:40:40/00:00:00:00:00/e0 Emask 0x2 (HSM violation)
[   29.484533] ata1.00: status: { DRDY }
[   29.484623] ata1: soft resetting link
[   29.648102] ata1.00: NODEV after polling detection
[   29.648107] ata1.00: revalidation failed (errno=-2)
[   34.640074] ata1: soft resetting link
[   34.804104] ata1.00: NODEV after polling detection
[   34.804110] ata1.00: revalidation failed (errno=-2)
[   39.796082] ata1: soft resetting link
[   39.960105] ata1.00: NODEV after polling detection
[   39.960111] ata1.00: revalidation failed (errno=-2)
[   39.960190] ata1.00: disabled
[   39.960237] ata1: soft resetting link
[   40.116114] ata1: EH complete
[   78.192061] Clocksource tsc unstable (delta = -96772823 ns)

```I run a AMD64 with 32 bit Maverick Meerkat
ATI radeon 1200x

Thanx in advance

---

### Post by leapinglangoor on 2011-04-15
bump

---

### Post by KegHead on 2011-04-15
Hi!

It could be your video card..

How much ram do you have?

KegHead

---

### Post by leapinglangoor on 2011-04-15
1 gb. Doubt its a hardware problem. Works fine long as I run 'compiz check' after startup

---

### Post by KegHead on 2011-04-15
Hi!

video card drivers.

Ke

---

