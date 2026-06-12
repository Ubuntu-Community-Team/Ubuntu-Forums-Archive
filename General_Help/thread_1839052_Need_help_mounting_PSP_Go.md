---
title: "Need help mounting PSP Go"
date: 2011-09-04
forum: General Help
---

### Post by projectzro on 2011-09-04
Ok i have a PSP Go (N1001 model) with OFW 6.39 and temp CFW that goes away when restarted. Im running Ubuntu 11.04 on a CR-48 from google, with latest updates. 

When i put the PSP Go into usb mode and plug it in to the USB port nothing happens. I goto Computer:/// and i see my hard drive and an MP3 player icon that says SONY "PSP" MS but i cant mount it (no option to) and cant see it in any of the media software. Nautilus cant open it either. there is no file system to be shown and is formatted to FAT16 (done by the psp itself by default) there is no memory card in it but its a psp go so there is 16GB internal memory. 

i know its not the PSP or the memory in it. my Windows machine sees it just fine. and its not the cable i used it 20 minutes ago (in fact it's brand new) 

additional info: 
it does not show up in the device list:
```
Michaell@cr-48-ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.9G  5.0G  4.5G  53% /
devtmpfs              948M  500K  947M   1% /dev
none                  948M  2.0M  946M   1% /dev/shm
none                  948M  248K  948M   1% /var/run
none                  948M     0  948M   0% /var/lock

```

i Have also tried this in Ubuntu 10.10

any help would be awesome.

---

### Post by projectzro on 2011-09-05
this is an error i got when i right clicked on the icon labeled "SONY "PSP" MS" and selected safely remove device



```
Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory
```

---

