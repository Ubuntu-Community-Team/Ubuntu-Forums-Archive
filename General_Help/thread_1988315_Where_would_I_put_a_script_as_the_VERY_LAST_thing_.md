---
title: "Where would I put a script as the VERY LAST thing to do before shutdown?"
date: 2012-05-27
forum: General Help
---

### Post by gopher38 on 2012-05-27
Hi,

Not sure if there's a way to do this, but I thought I'd ask.

Here's my situation.  I have Lucid running on an external USB HD.  Runs great. The only issue I have is that ubuntu leaves the disk running on shutdown.  This is probably normal, since the OS is on the external disk, it can't really shut it down, since the whole thing would die right then and there.  I don't want to leave it running however, so I'm trying to find some way to spin it down as the last step before shutdown.  

I've read some threads that say that the command to use to spin down an external disk is sdparm.

I've also found some threads that say to put the script to do that in crontab (won't work), or the bash profile (wont' work), or init.d.  I suppose that (if it will work at all), it would go in init.d, but does anyone know:
a) is there somewhere that I could put it that would execute even later than the init.d shutdown scripts?
b) if it does go into initd., where I'd put it and what I'd name it so that it only runs on shutdown and runs as late as possible (preferably the last thing to run)?

Muchas gracias.

---

### Post by lechien73 on 2012-05-27
I would probably suggest putting it in the /etc/rc6.d directory. Since you want it to be the last thing run before reboot, then you could name it S80spindown or something like that (since on my system S90reboot is the last script, and they're executed sequentially).

The only problem I'd foresee is whether you run it before you unmount root or after. If after, would you still have access to the executable file? If before, would that prevent the other scripts from running?

---

### Post by efflandt on 2012-05-27
Sounds like you have an externally powered drive, because portable USB drives based on laptop drives (powered from USB) typically shut down when the OS does.

I have heard of **hdparm** for doing things like that (which should be on your system by default), but never heard of **sdparm** ( nothing about it, nor suggestions for packages to install, in "man").

**man hdparm** (in a terminal)

But I would not try to spin down the drive immediately in case something still needs to be read from the disk.  I would use hdparm -S (capital S) to set the drive timeout for idle (low power) and spindown.  That may not stop it immediately, but at least it should not run forever.

If you set a very short time you might want to disable that (-S 0) or set a longer time when booting up (long enough that logging would keep it spun up).

---

