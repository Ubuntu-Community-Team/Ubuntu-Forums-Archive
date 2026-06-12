---
title: "No sound in usb headset in ubuntu maverick"
date: 2011-02-03
forum: General Help
---

### Post by zelalem on 2011-02-03
Hi all I have a USB headset and coudn't get any sound. I had googled all around and had it working after setting the asound.conf file, but the following day when the system restarts it stoped bring sound. I have installing different packages (puse audio, padevchooser, pavucontrol, and asoundconf-gtk). The output of lsusb is the following:

zelalem@zelalem-desktop:~$ lsusb
Bus 002 Device 007: ID 046d:c313 Logitech, Inc. 
Bus 002 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 005: ID 046d:c05b Logitech, Inc. 
Bus 002 Device 004: ID 0d8c:000c C-Media Electronics, Inc. Audio Adapter
Bus 002 Device 003: ID 1307:0330 Transcend Information, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:09a4 Logitech, Inc. QuickCam E 3500
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Please advice me what must i do. There is no sound in VLC or on firefox. I have already flash installed. I spent two days figuring out what I can do.

Thanks a lot.

Zelalem

---

### Post by zelalem on 2011-02-03
Hi finally I got it working. inside Alsamixer window, I chose F6 (select sound card) and increased the volume and it worked. The problem is when the system restarts i should do it again as I find the volume diminished. Anyway at least i can now hear sound.

---

