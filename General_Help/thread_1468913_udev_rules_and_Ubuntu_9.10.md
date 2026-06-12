---
title: "udev rules and Ubuntu 9.10"
date: 2010-05-01
forum: General Help
---

### Post by timdf911 on 2010-05-01
I had my udev rules working well with Ubuntu 8.10, see rules below, but in 9.10 it seems something has changed and I can't make them work anymore - no matter if I put them under /etc or /lib or at any priority.

I've googled and searched many times but not found a solution which works.


It's a pain when I have to re-boot for some reason and all the video sources swap round !

Does anyone have any idea what I'm doing wrong ?  I suspect it maybe a permission problem as the symlink's don't get created.


KERNEL=="video[0-9]*", SYSFS{name}=="BT878 video (ProVideo PV150)", SYSFS{subsystem_device}=="0x1460", NAME="video0", SYMLINK+="backdoor"
KERNEL=="video[0-9]*", SYSFS{name}=="BT878 video (ProVideo PV150)", SYSFS{subsystem_device}=="0x1461", NAME="video1", SYMLINK+="sidegate"
KERNEL=="video[0-9]*", SYSFS{name}=="BT878 video (ProVideo PV150)", SYSFS{subsystem_device}=="0x1462", NAME="video2", SYMLINK+="frontdoor"
KERNEL=="video[0-9]*", SYSFS{name}=="BT878 video (ProVideo PV150)", SYSFS{subsystem_device}=="0x1463", NAME="video3", SYMLINK+="backyard"

---

