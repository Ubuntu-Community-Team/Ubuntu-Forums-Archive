---
title: "excessive repetitive dmesg logging"
date: 2010-03-11
forum: General Help
---

### Post by MichaelBurns on 2010-03-11
Apparently, my dmesg log is being written to with the same message over and over again:

```

[15709.392102] sd 5:0:0:0: [sdb] Sense not available.
[15709.392182] sd 5:0:0:0: [sdb] Write Protect is off
[15709.392188] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[15709.392194] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[15709.392545] sd 5:0:0:0: [sdb] READ CAPACITY failed
[15709.392550] sd 5:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK

```

As best I can estimate, this is consuming about 3 kB/sec.

I suspect that this is related to a problem that I've been having with usb.  I was checking the dmesg log to figure out the usb problem.  The log was behaving itself (i.e. not writing anything).  When I pulled out my 8 GB flash stick, the above message started repeating itself to the dmesg log.

---

### Post by MichaelBurns on 2010-03-20
I forgot to ask a question in my OP.

How can I stop dmesg logging?

---

### Post by dcstar on 2010-03-20
> **MichaelBurns said:**
> Apparently, my dmesg log is being written to with the same message over and over again:

```

[15709.392102] sd 5:0:0:0: [sdb] Sense not available.
[15709.392182] sd 5:0:0:0: [sdb] Write Protect is off
[15709.392188] sd 5:0:0:0: [sdb] Mode Sense: 00 00 00 00
[15709.392194] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[15709.392545] sd 5:0:0:0: [sdb] READ CAPACITY failed
[15709.392550] sd 5:0:0:0: **[sdb]** Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK

```

As best I can estimate, this is consuming about 3 kB/sec.

I suspect that this is related to a problem that I've been having with usb.  I was checking the dmesg log to figure out the usb problem.  The log was behaving itself (i.e. not writing anything).  **When I pulled out my 8 GB flash stick**, the above message started repeating itself to the dmesg log.

And did you unmount it correctly before removing it?

---

### Post by MichaelBurns on 2010-03-21
Thanks for the response, dcstar.

> **dcstar said:**
> And did you unmount it correctly before removing it?I believe so, but I can't be sure.  I didn't just pull it out, if that's what you mean.  I clicked the eject symbol next to it in nautilus, and the mount point (/media/UFD008P3) disappeared.  Regardless, I would rather not get distracted in this thread with the usb issue.  (I already have another thread for the usb issue that no one seems interested in.)

I would like to find out how to recover from such a runaway dmesg disaster, regardless of how it happens, if that's possible.

---

### Post by MichaelBurns on 2010-06-28
bump

---

### Post by MichaelBurns on 2010-11-20
I am still interested in fixing this dmesg problem, just for my own understanding.  However, FYI:

I have upgraded to Xubuntu 10.04 live usb with persistence (with a whole new set of problems, for other threads).  I finally figured out how to get it to work on my laptop that can't even boot to usb.  For those of you who are interested, I use a cd with Plop installed.  It is very straightforward (even I got it to work).  Of course, I had to finally use someone else's computer to create the Plop disk, but other than than I was able to do it all from my own laptop.

---

### Post by dcstar on 2010-11-20
> **MichaelBurns said:**
> Thanks for the response, dcstar.

I believe so, but I can't be sure.  I didn't just pull it out, if that's what you mean.  I clicked the eject symbol next to it in nautilus, and the mount point (/media/UFD008P3) disappeared.  Regardless, I would rather not get distracted in this thread with the usb issue.  (I already have another thread for the usb issue that no one seems interested in.)

I would like to find out how to recover from such a runaway dmesg disaster, regardless of how it happens, if that's possible.

Such errors appear when you have a faulty USB device that is not responding as Ubuntu expects.

USB stick drives have a limited lifespan, do not assume that they will work forever.

---

### Post by MichaelBurns on 2010-12-07
bump
> **MichaelBurns said:**
> ... I would rather not get distracted in this thread with the usb issue.
...
**I would like to find out how to recover from such a runaway dmesg disaster, regardless of how it happens, if that's possible.**For example, I'm hoping that there is some simple command that I just don't know about, like
```

ubuntu@ubuntu:~$ kill_dmesg

```

---

