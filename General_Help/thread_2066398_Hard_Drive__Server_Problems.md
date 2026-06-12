---
title: "Hard Drive / Server Problems"
date: 2012-10-04
forum: General Help
---

### Post by sdpagent on 2012-10-04
Dear all,

I have been having some issues with my remote machine that I use to store hard drives and display on-screen information about them.
If I run this command:
```
udevadm info -q all -n /dev/sdd
```I get only the following output, instead of loads of information about the drive:
```
P: /devices/pci0000:80/0000:80:01.0/0000:82:00.0/host7/port-7:2/end_device-7:2/target7:0:2/7:0:2:0/block/sdd
N: sdd
E: DEVNAME=/dev/sdd
E: DEVPATH=/devices/pci0000:80/0000:80:01.0/0000:82:00.0/host7/port-7:2/end_device-7:2/target7:0:2/7:0:2:0/block/sdd
E: DEVTYPE=disk
E: MAJOR=8
E: MINOR=48
E: SUBSYSTEM=block
E: UDEV_LOG=3
```Also if I run 
```
smartctl --all /dev/sdd
```the terminal just 'hangs' and I cant even cntrl-c out and have to start another.
The same applies if I run:
```
hdparm -I /dev/sdd
```Also, ever since I plugged in about 24 additional drives into this machine (one of which is bound to be /dev/sdd but I cant figure out which one), ubuntu will not shut down from the terminal command, and it wont auto-log into the gui session and then start the vino-server like I had set it to on startup. To reboot the machine I have had to run IPMI power shut off commands.  However I have been able to ssh in to the machine for trying to diagnose the issue(s).

Can anyone shed some light whether whatever /dev/sdd could be stopping ubuntu from starting up/shutting down correctly? Could /dev/sdd just be a corrupt drive? Are there other terminal commands I could use to try and find out whats in /dev/sdd?

Any help appreciated,
Stu

---

