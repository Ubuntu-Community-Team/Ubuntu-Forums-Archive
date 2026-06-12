---
title: "System Freeze and led error code"
date: 2009-10-07
forum: General Help
---

### Post by tom.swartz07 on 2009-10-07
Hi all,

Ive been having this strange problem occur recently, and I have been unable to nail down the source.

Every so often, for what seems to be no explicable reason, my system locks up, and the CAPS lock and Num lock LEDs flash 10 times, pause, then repeat.

I was wondering if anyone could help provide assistance in finding the source of this problem, as I must hard-reset the system each time this happens.

My computer is a Dell Inspiron 1521, and searching through the documentation provided no such error code. 
Im running Ubuntu 9.04, with AMD 64bit processors.

The only common denominator that I could think of between any of these instances is the fact that I am running Transmission.


Any Ideas? Where could I go to get a system error log to traceback the problem?

Thanks,
Tom

---

### Post by alphaniner on 2009-10-07
I'm pretty sure the flashing LEDs indicate a kernel panic.  System logs are located in /var/log, but I'm not familiar with most of the logs there.

Also, I'm not sure if it works after a panic, but you could try

Alt+SysRq REISUB

if it happens again.  That is

Press and hold Alt
Press and hold SysRq 
Type REISUB (leaving about a second between each keystroke)

---

### Post by tom.swartz07 on 2009-10-07
> **alphaniner said:**
> I'm pretty sure the flashing LEDs indicate a kernel panic.  System logs are located in /var/log, but I'm not familiar with most of the logs there.

Also, I'm not sure if it works after a panic, but you could try

Alt+SysRq REISUB

if it happens again.  That is

Press and hold Alt
Press and hold SysRq 
Type REISUB (leaving about a second between each keystroke)

Ive poked around in the /log/ folder but I couldnt see anything that would be related to the crash- maybe I just missed it?

Specifically, what does that command do? ```
Alt+SysRq REISUB
```

---

### Post by alphaniner on 2009-10-07
I was thinking kern.log, debug, and maybe syslog would be good placed to look, but like I said I'm not really familiar with them.

Briefly, Alt+SysRq REISUB does the following:

R: Switch the keyboard from raw mode to XLATE mode
E: Send the SIGTERM signal to all processes except init
I: Send the SIGKILL signal to all processes except init
S: Sync all mounted filesystems
U: Remount all mounted filesystems in read-only mode
B: Immediately reboot the system, without unmounting partitions or syncing

For more detailed information, go [here]("http://www.google.com").

---

### Post by tom.swartz07 on 2009-10-07
Right now, the syslog, kern.log, etc files are all filled up with entries from everything so far today. I cannot trace back any farther than 7.30am, whereas the kernel panic occurred sometime between 12am-7am.

Ill see if I could replicate the problem, and then check the logs.

Thanks!

---

### Post by alphaniner on 2009-10-07
You could also try the archived logs (the ones with .# and .#.gz).  The ones with .gz are compressed, you can read them directly with **zcat** or **zless** ie.

```
zcat kern.log.1.gz
zless kern.log.1.gz
```

---

### Post by tom.swartz07 on 2009-10-07
Just happened again.
This time, I only had Google Chrome dev-build open.

Here is Kern.log for the 2 minutes up to the time it happened.

```
Oct  7 16:28:04 ubuntu-laptop kernel: [   30.796283] ppdev: user-space parallel port driver
Oct  7 16:28:04 ubuntu-laptop kernel: [   31.072501] [drm] Initialized drm 1.1.0 20060810
Oct  7 16:28:04 ubuntu-laptop kernel: [   31.404999] [drm] Initialized radeon 1.29.0 20080528 on minor 0
Oct  7 16:28:04 ubuntu-laptop kernel: [   32.114135] [drm] Setting GART location based on new memory map
Oct  7 16:28:04 ubuntu-laptop kernel: [   32.114400] [drm] Loading RS690/RS740 Microcode
Oct  7 16:28:04 ubuntu-laptop kernel: [   32.114470] [drm] Num pipes: 1
Oct  7 16:28:04 ubuntu-laptop kernel: [   32.114477] [drm] writeback test succeeded in 1 usecs
Oct  7 16:28:07 ubuntu-laptop kernel: [   34.381139] ADDRCONF(NETDEV_UP): eth0: link is not ready
Oct  7 16:28:11 ubuntu-laptop kernel: [   39.105021] eth1: no IPv6 routers present
Oct  7 16:29:05 ubuntu-laptop kernel: [   93.001035] Clocksource tsc unstable (delta = -184871683 ns)
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532714] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532725] ata5.00: ST_FIRST: !(DRQ|ERR|DF)
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532741] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532744]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532747]          res 50/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532754] ata5.00: status: { DRDY }
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.532797] ata5: soft resetting link
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.757560] ata5.00: configured for UDMA/33
Oct  7 16:29:12 ubuntu-laptop kernel: [   96.771920] ata5: EH complete
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537170] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537182] ata5.00: ST_FIRST: !(DRQ|ERR|DF)
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537198] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537200]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537203]          res 50/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537210] ata5.00: status: { DRDY }
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.537251] ata5: soft resetting link
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.761555] ata5.00: configured for UDMA/33
Oct  7 16:29:53 ubuntu-laptop kernel: [  140.780958] ata5: EH complete
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436118] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436129] ata5.00: ST_FIRST: !(DRQ|ERR|DF)
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436145] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436148]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436150]          res 50/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436158] ata5.00: status: { DRDY }
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436238] ata5: soft resetting link
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.664940] ata5.00: configured for UDMA/33
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.679978] ata5: EH complete
```

The Syslog shows a lot of activity on my wifi card (eth0), but there doesnt seem to be anything out of the ordinary there. Ill post it if you want?

---

### Post by tom.swartz07 on 2009-10-07
For reference, the lockup and LED flashing code occurred at 16:30

I still cant figure out why its doing this!

---

### Post by alphaniner on 2009-10-07
Don't post it for my sake.  Like I said, I have very little experience with this kind of thing.

That said, I can't help but notice

```
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436118] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436129] ata5.00: ST_FIRST: !(DRQ|ERR|DF)
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436145] ata5.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436148]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436150]          res 50/00:01:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436158] ata5.00: status: { DRDY }
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.436238] ata5: soft resetting link
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.664940] ata5.00: configured for UDMA/33
Oct  7 16:30:21 ubuntu-laptop kernel: [  168.679978] ata5: EH complete
```

Granted there's several occurrences, but they're all within a minute of the lockup.  Do you see this elsewhere in the log?

---

### Post by tom.swartz07 on 2009-10-07
> **alphaniner said:**
> 
Granted there's several occurrences, but they're all within a minute of the lockup.  Do you see this elsewhere in the log?

Thats partially the reason that I posted that rather than the syslog. Whatever these error codes mean, they all happen at the time up to and just before the system locks. The other entries into the log are stupid things like IP address and MAC IDs.

Is there anyone that might be able to shine some light into this subject? Maybe an Admin could break this off into another category where it would be more useful?

---

### Post by JeSTeR7 on 2009-10-07
Do you have a Broadcom wireless card?  Are you using the WL/STA driver?

---

### Post by tom.swartz07 on 2009-10-07
> **JeSTeR7 said:**
> Do you have a Broadcom wireless card?  Are you using the WL/STA driver?

Yep Broadcom with the Restricted STA driver.
Why?

---

### Post by JeSTeR7 on 2009-10-07
I think it has to do with that.  I've had problems in Jaunty with the exact same symptoms, and now I'm having it with Karmic beta.  

There are a couple of bugs in Launchpad about it, some even claiming its fixed.

There's nothing in the logs about the crash, and the Alt+SysRq doesn't work.  It simply crashes hard and you need to hard reboot the system.

---

