---
title: "Huawei Mounting Problem"
date: 2010-01-29
forum: General Help
---

### Post by thomas.livingston on 2010-01-29
[FONT=Calibri][SIZE=3]I have recentally installed 9.10 and cannot get my optus HUAWEI dongle to work( Mounting problems error 32) I have read some of the forms and there is alot of conflicting information if this can be fixed or not?[/SIZE][/FONT]

---

### Post by alexfish on 2010-01-29
hi

can you post some information

From the terminal try these codes 

Code:

lsusb

code:

  	 	 	 	 	 	  dmesg | grep -e "modem" -e "tty" 



''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

 
thanks in advance

---

### Post by thomas.livingston on 2010-02-01
[FONT=Arial][SIZE=3]From the terminal this is the info you requested [/SIZE][/FONT]
[COLOR=black][FONT=Verdana]thomas@thomas-laptop:~$ lsusb[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 002: ID 064e:a100 Suyin Corp. Acer OrbiCam[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thomas@thomas-laptop:~$ dmesg | grep -e "modem" -e "tty"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][    0.001683] console [tty0] enabled[/FONT][/COLOR]
Do you think it would be worth going back to 9.04

---

### Post by alexfish on 2010-02-04
hi

updating Ubuntu 9.10 to latest kernels -17 or -18 may help

if you have the original kernel try to disable the  the USB Storage kernel module


you can try from the terminal as root

**[B]rmmod usb-storage**[/B]


also consider installing the latest usb modeswitch :Latest package at 

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

use the latest integrated pkg 1.1.0


[LIST]
[*][SIZE=2]Usb ModeSwitch Latest debian Package [/SIZE]1.0.7-1
[*][SIZE=2]
[/SIZE]
[*][SIZE=2][http://packages.debian.org/sid/usb-modeswitch](http://packages.debian.org/sid/usb-modeswitch)[Package  ]("http://packages.debian.org/sid/usb-modeswitch")[/SIZE]
[/LIST]

---

