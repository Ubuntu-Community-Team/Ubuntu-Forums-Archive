---
title: "Removed Python 2.6, Corrupted GUI"
date: 2009-12-23
forum: General Help
---

### Post by VorpalAuroch on 2009-12-23
Hi, relative Ubuntu noob here. I'm having aproblem with Karmic Koala.

Recently I was running out of space on my netbook, so I went through removing programs I didn't need. I had both Python 3.0 and 2.6 installed, so I removed the redundant 2.6. The GUI immediately crashed, and when I rebooted it was corrupted.

Currently, its display is reminiscent of TV "snow," but usually in color. When I tried to run or install Ubuntu (this time Netbook Remix) off of a flash drive startup disc, it gets through the first few menus, but after I choose to install or run from disc, it goes to snow again.

I can get to recovery mode and to the command line, but I don't know what to do once I get there.

---

### Post by dcstar on 2009-12-23
> **VorpalAuroch said:**
> Hi, relative Ubuntu noob here. I'm having aproblem with Karmic Koala.

Recently I was running out of space on my netbook, so I went through removing programs I didn't need. I had both Python 3.0 and 2.6 installed, so I removed the redundant 2.6. The GUI immediately crashed, and when I rebooted it was corrupted.

Currently, its display is reminiscent of TV "snow," but usually in color. When I tried to run or install Ubuntu (this time Netbook Remix) off of a flash drive startup disc, it gets through the first few menus, but after I choose to install or run from disc, it goes to snow again.

I can get to recovery mode and to the command line, but I don't know what to do once I get there.
Assuming your network is functional:
```
sudo apt-get install python2.6
```

---

### Post by VorpalAuroch on 2009-12-24
> **dcstar said:**
> Assuming your network is functional:
```
sudo apt-get install python2.6
```

Tried this. No change.

---

### Post by lukeiamyourfather on 2009-12-24
Python 2.X to 3.X has some changes that break compatibility so they can't be used interchangeably. Most everything still uses Python 2.X which is why its the default in Ubuntu. The Python 2.6 package is absolutely required to run Ubuntu. The Python 3.X package is optional for early adopters, but the older Python 2.X package is still required to run everything else. If reinstalling Python 2.6 didn't fix it, then it'd probably be easier to just reinstall the system than troubleshooting all of the other broken things that relied on Python. Cheers!

---

### Post by VorpalAuroch on 2009-12-24
> **lukeiamyourfather said:**
> Python 2.X to 3.X has some changes that break compatibility so they can't be used interchangeably. Most everything still uses Python 2.X which is why its the default in Ubuntu. The Python 2.6 package is absolutely required to run Ubuntu. The Python 3.X package is optional for early adopters, but the older Python 2.X package is still required to run everything else. If reinstalling Python 2.6 didn't fix it, then it'd probably be easier to just reinstall the system than troubleshooting all of the other broken things that relied on Python. Cheers!

How can I reinstall the system? When I try to reinstall off a startup disk, I still have the graphics problem and can't see anything.

---

### Post by lukeiamyourfather on 2009-12-24
> **VorpalAuroch said:**
> How can I reinstall the system? When I try to reinstall off a startup disk, I still have the graphics problem and can't see anything.

Did the graphics work when originally booting from the installer? Its possible the computer is still booting to the disk rather than the installer.

---

### Post by VorpalAuroch on 2009-12-24
> **lukeiamyourfather said:**
> Did the graphics work when originally booting from the installer? Its possible the computer is still booting to the disk rather than the installer.

I see the first couple menus, so I know it's booting off the disk. After it tries to install or just run off of the flash drive, it dies. Is it possible that the disc's become corrupted? If it has, would recreating the boot disk from another computer fix the problem?

---

### Post by lukeiamyourfather on 2009-12-24
> **VorpalAuroch said:**
> I see the first couple menus, so I know it's booting off the disk. After it tries to install or just run off of the flash drive, it dies. Is it possible that the disc's become corrupted? If it has, would recreating the boot disk from another computer fix the problem?

Its worth a try. Could also be the graphics chipset is failing coincidentally and the two are unrelated.

---

