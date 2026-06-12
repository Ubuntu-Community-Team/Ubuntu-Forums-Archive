---
title: "connect-debounce error"
date: 2010-02-21
forum: General Help
---

### Post by Coach_Mark on 2010-02-21
i got the wierdest messages the other day.  i went to shut down a Dell Inspirion 1545 laptop, and about halfway through the little yellow/orange bar the screen went black and it said:
 
"xxx.xxxxxx hub 2.0: 1.0 connect-debounce failed port y disabled" (xxx.xxxxxx being a different number string each time, and y being a port number)
 
it gives me that message for 3, sometimes 4, ports--3 times (port 2, port 3, port 1, port 2, port 3, port 1, etc.).  
 
Once I got that while starting up.  Near the end of that colored bar, it gave me the black screen, and then this big long list of stuff it was checking.  When it got to starting Bluetooth, it started that connect-debounce thing for all the ports.  then there was some other stuff that disappeared faster than I could write it down.  however, Ubuntu did a system check the next day, and that start up issue disappeared--at start up and shut down.  

a couple of days ago, it started the connect-debounce thing on shutdown again.  Ubunutu did a system check Thursday, but it did not fix the shut down issue or get the USB mouse/items to work.  a friend suggested I post the below output.

coach@coach-laptop:~$ tail -f /var/log/messages
Feb 21 15:06:13 coach-laptop -- MARK --
Feb 21 15:26:13 coach-laptop -- MARK --
Feb 21 15:46:13 coach-laptop -- MARK --
Feb 21 16:06:13 coach-laptop -- MARK --
Feb 21 16:26:13 coach-laptop -- MARK --
Feb 21 16:46:13 coach-laptop -- MARK --
Feb 21 17:06:13 coach-laptop -- MARK --
Feb 21 17:26:13 coach-laptop -- MARK --
Feb 21 17:46:13 coach-laptop -- MARK --
Feb 21 18:03:59 coach-laptop kernel: [385082.408075] usb 2-2: USB disconnect, address 44


anyone know what happened and/or how to fix it?

---

### Post by SaikoRonin on 2010-02-24
I have a similar issue on my Intel-E4300 chipset computer..

It started by making my usb mouse fail, followed by the printer and other usb ports.  

A cold reboot fixed this once but failed to fix it on subsequent reboots.

Downgrading from Lucid to Jaunty Jackalope did not help either.

> ronin@ronin-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
ronin@ronin-desktop:~$ 


> ronin@ronin-desktop:~$ dmesg 
[ 1038.408029] hub 1-0:1.0: connect-debounce failed, port 7 disabled


(that error repeats endlessly)

---

### Post by maznos on 2010-03-25
I have same problem

What is the problem with this issue

---

### Post by abhiramcr on 2010-05-08
[SIZE=2]can someone help here?
I'm only new to Linux, and don't know much, except for some exploring i did. from my kernel log file (kern.log) i figure out that something is very periodically being polled, but i'm not able to find out which port is it looking for. 
the error message says so:
<stripping the time stamp and the PC-name>[COLOR=Red] [/COLOR][/SIZE][SIZE=2][COLOR=Red]**kernel: [ 6392.612049] hub 1-0:1.0: connect-debounce failed, port 6 disabled**[/COLOR]. [/SIZE][SIZE=2]I understand that the [6392.xxx] is to do with the time since log-in, but nothing beyond that. This continues even when i shut down my Linux. How do i find out which port has been disabled, and how is it that i can fix this issue...?

Any help will be greatly appreciated... :)
[/SIZE]

---

