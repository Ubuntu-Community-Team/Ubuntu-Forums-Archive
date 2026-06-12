---
title: "Clean mounting HFS+ partition after power failure"
date: 2012-07-16
forum: General Help
---

### Post by mszargar on 2012-07-16
I have a rather large external harddrive formatted in Apple's HFS+ format, and reformatting it is not an option for me. Now that I have a linux server at home, I have turned journalling off on the harddrive and I mount it with read and write access at boot time on my Ubuntu box (12.04 Desktop version, but I use it as a home print/file/media server). Up to here everything works smoothly.

The problems start when some event leads to an unclean unmount, and this happens a lot in a home environment. This can be a power failure, or a cable disconnection, or etc.... Consequently, the HFS+ drive does not mount anymore at boot time and if I try to mount it manually, it gets mounted as read-only. To solve the problem, every single time I have to disconnect the drive, and connect and mount it on my MacBook. After a clean unmount the drive can be mounted with no problem on my linux box.

Is there anyway to skip this connecting-to-osx-box step, i.e., is there anyway to clean mount an unclean unmounted HFS+ drive with read and write access in Ubuntu? Is there a switch that I can use in my fstab to force the mounting?

Thanks in advance. Mah

---

### Post by mszargar on 2012-07-16
[This]("http://usa.autodesk.com/adsk/servlet/ps/dl/item?linkID=9242618&id=15482178&siteID=123112") is the issue I am trying to avoid, except that nowadays you don't even need a fsck on MacOS to achieve a read/write mount. MacOS mounts the drive in read/write mode even if the HFSPLUS_VOL_INCNSTNT flag is set. I don't even know why Linux's hfsplus driver sets this flag, and conditions read/write mount to it, if MacOSX healthily ignores it?!

---

