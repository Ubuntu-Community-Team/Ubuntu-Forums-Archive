---
title: "unable to resolve host ubuntu on login"
date: 2012-08-22
forum: General Help
---

### Post by dougleduck on 2012-08-22
So somehow I've borked my ubuntu 12.04 (64 bit) system. I think somehow I uninstalled the wrong package last time I was logged in, and somehow ubuntu-desktop/unity got messed up.

Currently booted into 11.10 64bit usb liveCD, which has internet access. I'm trying to do an apt-get update while chrooted into my hard disk install but while chrooted it can't seem to see the internet connection so I get hundred of errors of the type
[INDENT]Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
[/INDENT]

---

### Post by coldcritter64 on 2012-08-22
> **dougleduck said:**
> So somehow I've borked my ubuntu 12.04 (64 bit) system. I think somehow I uninstalled the wrong package last time I was logged in, and somehow ubuntu-desktop/unity got messed up.

Currently booted into 11.10 64bit usb liveCD, which has internet access. I'm trying to do an apt-get update while chrooted into my hard disk install but while chrooted it can't seem to see the internet connection so I get hundred of errors of the type[INDENT]Something wicked happened resolving 'gb.archive.ubuntu.com:http' (-5 - No address associated with hostname)
[/INDENT]
As part of the steps to set up a live cd chroot in Lucid I would use the command
```
sudo mount -o bind /etc/resolv.conf /mnt/etc/resolv.conf
``` this part of the process should address your problem.

The full process I used in Lucid may help you, I've attached a text file  of the proceedure below, it has 2 options, full step by step process **or** compressed into 1 line of code to mount the chroot and 1 action and 1 line of code pasted to unmount the chroot.

---

