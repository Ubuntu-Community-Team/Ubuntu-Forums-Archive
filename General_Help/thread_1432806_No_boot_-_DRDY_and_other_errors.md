---
title: "No boot - DRDY and other errors"
date: 2010-03-18
forum: General Help
---

### Post by blackrock on 2010-03-18
I'm posting this in hope that someone knows the solution. I've Googled for it, asked on #ubuntu channel, tried various stuff, but no luck.

My system is Ubuntu 9.10, Linux 2.6.31-20-generic, and Gnome.

I could've done a fresh install, but I can't access my ecryptfs-encrypted home folder and recover my files :(

**Here are the error messages in normal mode:**

```
Could not update ICEauthority file /home/USERNAME/.ICEauthority
```and after that:
```
There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
```and after that:
```

Nautilus could not create the following required folders: /home/USERNAME/Desktop, /home/USERNAME/.nautilus.

Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.
```And after closing or pressing OK on each windows, there's just the default wallpaper and a mouse cursor, nothing else.

**When I try the recovery mode:**

```
...
fsck from util-linux-ng 2.16
/dev/sda1: clean, 405268/7028736 files, 21286046/28103701 blocks
 * Starting init crypto disks...                                       [OK]
**>>>waits here about a minute<<<**
[  101.816070] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[  101.816137] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  101.816138]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00 
[  101.816140]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[  101.816294] ata1.01: status: { DRDY }
```

---

### Post by Nick. on 2010-03-20
Yeah i'm getting exactly the same problem. I tried replacing the hard drive because i had an error earlier on warning me i had too many bad sectors. Didn't help at all :(. Getting seriously annoyed now. Sorry i couldn't help though.

---

### Post by frankiethepill on 2010-03-23
Same here. It's happened twice now, last time I reinstalled, but seems a long winded way to go about solving the problem. 

Linux claims to be the most stable system- it may be but is soooo complicated when it goes wrong or doesn't quite do what I want it to do. 
A few days ago I finally go the wireless going on my laptop, only to have an update this morning which meant I had to reinstall it, again. This isn't the way forward. I'm having to work so hard to keep the system running.

---

### Post by blackrock on 2010-03-26
I guess I'll just forget my precious files and reinstall the system :(

---

