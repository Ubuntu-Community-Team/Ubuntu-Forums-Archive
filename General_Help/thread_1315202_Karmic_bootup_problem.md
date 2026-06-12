---
title: "Karmic bootup problem"
date: 2009-11-05
forum: General Help
---

### Post by cnbiz850 on 2009-11-05
A few days ago I posted regarding issue related to VBox driver not being loaded after reboot. ([http://ubuntuforums.org/showthread.php?t=1303579]("http://ubuntuforums.org/showthread.php?t=1303579"))
Basically after every startup, I have to do: ```
sudo /etc/init.d/vboxdrv start
``` to get it started.
I thought it was a VBox problem, but it seems that the problem is not alone with VBox.  Found today that NFS server and printers are not properly started and I have to do similar things for them in order to get them working:```
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/cups start
```

I checked that both services are in /etc/rc2.d: ```
rc2.d:
README                 S20winbind     S70dns-clean       S99ondemand
S20dkms_autoinstaller  S25bluetooth   S70pppd-dns        S99rc.local
S20kerneloops          S50cups        S90binfmt-support  S99timidity
S20nfs-kernel-server   S50pulseaudio  S99acpi-support
S20speech-dispatcher   S50rsync       S99grub-common
S20vboxdrv             S50saned       S99laptop-mode

```

Why aren't they automatically started?  I am not sure what else are not normally started.  Can anyone please help on what is going on?

---

### Post by cnbiz850 on 2009-11-05
Found that the problem is due to a change in /etc/init.d/rc where I changed CONCURRENCY=none to CONCURRENCY=shell. Changed it back and things are normal now.

The reason for my earlier change was because I followed the advice from [Ubuntu Tips - Bootup Faster]("http://www.linuxlinks.com/article/20090927065957648/UbuntuTips-Booting-Part3.html").  Guess that is valid.  I do have multi-cores, but the comment in /etc/init.d/rc says that > the default boot sequence in Debian as of 2008-01-20 does not support concurrent booting.

---

