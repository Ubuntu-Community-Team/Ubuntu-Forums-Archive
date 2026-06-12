---
title: "bluetooth on HP DV4000 not working completely"
date: 2006-04-02
forum: General Help
---

### Post by dmorlow on 2006-04-02
Ok, about half of the time, I can get my wireless bluetooth mouse working on my HP laptop using the integrated bluetooth.  Right now, I can't get it to work again.  Here's the output when I run the commands in the terminal window. 

dorlow@ubuntu:~$ hidd --search
Searching ...

(right here, it usually sits here for about 15 seconds and then after I hit the connect button on my mouse, it comes back with an address and starts working.  Right now, it says the searching... and then immediately goes back to a new command prompt line)

dorlow@ubuntu:~$ sudo apt-get install bluez-utils
Password:
Reading package lists... Done
Building dependency tree... Done
bluez-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dorlow@ubuntu:~$ su root
Password:
root@ubuntu:/home/dorlow# sudo /etc/init.d/bluez-utils restart
 * Restarting Bluetooth services...                                      [ ok ]
root@ubuntu:/home/dorlow# lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 03f0:4b11 Hewlett-Packard
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 001 Device 001: ID 0000:0000
root@ubuntu:/home/dorlow# hcitool dev
Devices:

It should be showing something here I think

root@ubuntu:/home/dorlow# hidd --search
Searching ...
root@ubuntu:/home/dorlow#


To get this to work, sometimes just restarting my computer a few times works.  Then I go in and do an hidd --search, hit the connect button and it connects as slick as can be.  Today I cant get it to work... Go figure.

---

