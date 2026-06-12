---
title: "Optus Huawei mounting poblem"
date: 2010-02-02
forum: General Help
---

### Post by thomas.livingston on 2010-02-02
[COLOR=black][FONT=Verdana]9.10 Issue[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am unable connect to the internet via my optus huawei dongle but i can still explore the device when go to open the run file the following message apeers:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]Unable to mount Optus Wireless [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Error mounting: mount exited with exit code 32: mount: block device /dev/sr1 is write-protected, mounting read-only[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]mount: /dev/sr1 already mounted or /media/Optus Wireless busy[/FONT][/COLOR]
[FONT=Calibri][SIZE=3][COLOR=#00000a]From the termina information i have gathered [/COLOR][/SIZE][/FONT]
[COLOR=black][FONT=Verdana]thomas@thomas-laptop:~$ lsusb[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 002: ID 064e:a100 Suyin Corp. Acer OrbiCam[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]thomas@thomas-laptop:~$ dmesg | grep -e "modem" -e "tty"[/FONT][/COLOR]
[COLOR=black][FONT=Verdana][ 0.001683] console [tty0] enabled[/FONT][/COLOR]
Does [/FONT][/COLOR]

---

