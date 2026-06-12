---
title: "mount usb headphones"
date: 2011-03-01
forum: General Help
---

### Post by Arkish0 on 2011-03-01
i just got this arw200 acoustic research headphones

[http://www.pcrush.com/images/hi-res/391549.jpg](http://www.pcrush.com/images/hi-res/391549.jpg)

the problem is (as you can see) they only connect via USB port. 

when i type sudo fdisk -l i dont see them, but if I type on terminal 

~$ sudo lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 007 Device 006: ID 0d8c:0102 C-Media Electronics, Inc. CM106 Like Sound Device**
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0718:1900 Imation Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

how can i mount them?? how can i get ubuntu to reconize them as headphones??

BTW im using 10.04 .. 32bit

---

### Post by lfforman on 2011-03-01
Hi,
I have a USB logitech headphone, and there is no need to give any command to mount it, The first Time I used I went to sound preferences and it was atomatically recognized, I just had to set the output to be made by them with a click of a mouse.

---

### Post by powertower on 2011-03-01
You should be able to go under system -. preferences -> sound -> output and change to your usb headphones.

fdisk -l will not list usb headphones, it lists attached drives. You don't mount headphones.

---

### Post by Arkish0 on 2011-04-24
thanks!! that did it!!! =)

---

