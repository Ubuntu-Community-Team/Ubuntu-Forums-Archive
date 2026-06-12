---
title: "Broken after software update"
date: 2011-06-15
forum: General Help
---

### Post by shnplr on 2011-06-15
Hi,

I'm just getting back into Linux after (quite) a few years away; from Fedora Core2/3.  Trialling Ubuntu Natty with Unity and Linux Mint 11 running for 2 weeks.

So last night I clicked on the (Mint 11) Software Update Manager - a small shield appearing on the taskbar which listed about 30 pkgs to be updated. I've no idea what all these lib-xyq-012 files are but I thought, well the system is basically asking me to update my system, so why not?

A few minutes later it finished, and I went to my VPN connection but nothing happened.  I rebooted and noticed some errors displayed during shutdown but I didn't catch them.

After reboot:
a) date time has disppeared from the taskbar
b) network connections icon disappeared from taskbar
c) no internet connection at all!
d) menu --> system --> network manager --> (nothing happens)??

If anyone has some idea what I could try? (install Natty might be a valid solution at this point).  I searched the forums but couldn't see anyone else had this issue (is updating recommended updates from software update manager not a good idea?)

I don't have internet it's difficult to use the usual "google-and-resolve" approach, I have to keep booting back into WinXP.  I'd appreciate any suggestions - I'd like to know what broke and why, as well as restore my network connections (hopefully the VPN is still there too).

Thanks,

Paul

---

### Post by StrayEddy on 2011-06-15
Maybe the easiest way, repair with a Mint 11 liveCD

---

### Post by shnplr on 2011-06-18
My fault. I'd added dapper to the repository list to install JDK5 and forgot to remove before running software update.  There were 2 packages replaced which I reinstalled by booting from live dvd, performing chroot and issuing:

```
sudo apt-get install libnss3=3.12.9+ckbi-1.82-0ubuntu2
sudo apt-get install libnspr4=4.8.7-0ubuntu1

```

---

