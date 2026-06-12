---
title: "HP7450 stopped printing after installing update"
date: 2009-10-26
forum: General Help
---

### Post by woody1 on 2009-10-26
I ran updates a few days ago, now the hp7450 printer that was printing OK has started to give busy errors, then says job finished, but nothing prints not even a test . I am running Jaunty Jackalope .

lsusb gives

colin@june-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 07ab:fc84 Freecom Technologies 
Bus 001 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 03f0:0505 Hewlett-Packard ScanJet 2100c
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
colin@june-desktop:~$ 

It took ages to get this printer to work reliably, is it possible to undo the updates, or can anyone suggest a way to figure out what has gone wrong.

Thanks for your help,

                      Colin


Tried unplugging and replugging power to printer lsusb now gives

colin@june-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 03f0:b802 Hewlett-Packard Photosmart 7400 Series
Bus 001 Device 006: ID 07ab:fc84 Freecom Technologies 
Bus 001 Device 004: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 03f0:0505 Hewlett-Packard ScanJet 2100c
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
colin@june-desktop:~$ 

Tried printing again, page is still pending after 5 mins

---

