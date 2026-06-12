---
title: "Segmentation fault (core dumped)"
date: 2012-04-28
forum: General Help
---

### Post by pbeesley on 2012-04-28
Guys just like the below I'm getting Segmentation faults on a number of apps (ushare in the example below but also conky when trying to run gmail.py)

This is all being done on a clean install of 12.04 

```
kp3@SOL2:~$ ushare
Interface eth0 is down.
Recheck uShare's configuration and try again !
uShare (version 1.1a), a lightweight UPnP A/V and DLNA Media Server.
Benjamin Zores (C) 2005-2007, for GeeXboX Team.
See http://ushare.geexbox.org/ for updates.
Listening on telnet port 1337
Initializing UPnP subsystem ...
Starting in DLNA compliant profile ...
UPnP MediaServer listening on 192.168.0.14:49152
Sending UPnP advertisement for device ...
Listening for control point connections ...
Building Metadata List ...
Looking for files in content directory : /media/ICARAS/VIDEO
Segmentation fault (core dumped)
kp3@SOL2:~$
```

---

### Post by twshadow101 on 2012-04-29
I am having the same issue on Xubuntu 12.04

---

### Post by pbeesley on 2012-04-30
anyone got any ideas?

---

### Post by Cæncel on 2012-05-04
i'm also having this problem, using xubuntu 12.04

---

### Post by ckouris84 on 2012-05-15
This has been happening repeatedly to me with 12.04 LTS Server. I though that maybe if I did a fresh install from the .iso insteading of "do-release-upgrade" that it would fix...and all night for nothing!

I had to go back to 11.04 LTS Server because of this and now I am back to normal.

The issue I have is that when my php script uses curl_exec with HTTPS that it fails with a Segmentation fault (core dump) and no matter what I do!

I tried installing php-gdb and I ran a debug session with my script to find out that it's a libcrypto issue...did some research and think it might be openssl related.

I would love to see a fix...but until then I am back to the older Server release.

Anybody else?

:(

---

### Post by scratch178 on 2012-05-26
$ conky
Conky: desktop window (2400023) is subwindow of root window (15d)
Conky: window type - desktop
Conky: drawing to created window (0x2a00001)
Conky: drawing to double buffer
Segmentation fault (core dumped)


same problem here

any solutions jet?

---

### Post by Bersam on 2012-05-26
I have same problem here, I can't start Blender. :/
```

% blender
[1]    2214 segmentation fault (core dumped)  blender

```

---

### Post by Bersam on 2012-05-27
> **Bersam said:**
> I have same problem here, I can't start Blender. :/
```

% blender
[1]    2214 segmentation fault (core dumped)  blender

```
just in case, last week i could open it without any problem but now it just show me (core dumped)

---

### Post by Lubelaczek on 2012-06-14
> **pbeesley said:**
> anyone got any ideas?

Have same problem but there is a workaround that helps me. It is lame but...
I start 12.04 and wait until HD led is finally off or at least is not blinking every fraction of a second. Then I open Firefox (google is my home page). After a few seconds I start my Conky and it works. Few times resisted to, but I simply rebooted whole system  again and usualy conky starts after this whole trick. It will not start at all if I don't open Firefox before conky. Later I can close it without loosing Conky. Maybe thanks to this some of you who have more knowledge will get idea what/why/where to fix.

---

### Post by jk-menifee on 2012-08-06
The Firefox workaround mentioned in the message just above this one works for me too.

---

