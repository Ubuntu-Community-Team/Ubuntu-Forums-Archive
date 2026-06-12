---
title: "need help: ubuntu 11.04 crash when ending X pid"
date: 2011-06-17
forum: General Help
---

### Post by enjoyubt on 2011-06-17
[SIZE=3]My Foxconn nettop NT-A3500 crashed.[/SIZE]

[SIZE=3]I install Ubuntu 11.04 and enter it. Then I install all available updates(in the update manager), activate AMD/ATI closed source GPU driver(under hardware drivers).[/SIZE]

[SIZE=3]Then I do a reboot(sudo reboot). Then I login and do a VT switch to ex:tty2(CTRL + ALT + F2). Then I input the command[/SIZE]
[SIZE=3]"Localhost$ sudo pidof X" [/SIZE]

[SIZE=3]will show the pid I have to kill(kill as root or sudo). Then I kill the pid and the NT-A3500 would crash(usually on first try). [/SIZE]
 
**[SIZE=3]What is the problem?[/SIZE]**

---

### Post by enjoyubt on 2011-06-17
PS:
 
This is my detailed HARDWARE: 
CPU: AMD E350 DUAL CORE 1.6GHz APU
 
Memory:Asint SSY 3128M8-EAJ1D 2GB 1333
 
HDD: Western Digital WD3200BEVT 2.5'' Hard Disk Device/ SATA
 
VGA:AMD Radeon HD  6310

---

### Post by wildmanne39 on 2011-06-18
> **enjoyubt said:**
> [SIZE=3]My Foxconn nettop NT-A3500 crashed.[/SIZE]

[SIZE=3]I install Ubuntu 11.04 and enter it. Then I install all available updates(in the update manager), activate AMD/ATI closed source GPU driver(under hardware drivers).[/SIZE]

[SIZE=3]Then I do a reboot(sudo reboot). Then I login and do a VT switch to ex:tty2(CTRL + ALT + F2). Then I input the command[/SIZE]
[SIZE=3]"Localhost$ sudo pidof X" [/SIZE]

[SIZE=3]will show the pid I have to kill(kill as root or sudo). Then I kill the pid and the NT-A3500 would crash(usually on first try). [/SIZE]
 
**[SIZE=3]What is the problem?[/SIZE]**
It could be because of the process you are killing. Why are you killing a process?

---

