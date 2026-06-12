---
title: "Need help - how to get access to already created serial port/modem over bluetooth?"
date: 2012-06-07
forum: General Help
---

### Post by Artif on 2012-06-07
[COLOR=#000000][FONT=Sans]It  seems access to serial port services (on external devices) available over bluetooth  connections is blocked for ordinary user accounts (ver.12.04 Precise, files  /dev/rfcomm*). How to for ordinary user enable access to the ports?

As  ordinary user, with the help of blueman I can successfully connect over  bluetooth to service "serial port" of my mobile phone. As result I have  file /dev/rfcomm0, and I have read-write permission (via dialout  group).

Next I'm trying to use this dev.file as a GPRS modem serial port. I'm using wvdial:
```
$ wvdial --config=phone.conf
--> WvDial: Internet dialer version 1.61
--> Cannot open /dev/rfcomm0: Device or resource busy
--> Cannot open /dev/rfcomm0: Device or resource busy
--> Cannot open /dev/rfcomm0: Device or resource busy
``````
$ echo "AT" > /dev/rfcomm0
bash: /dev/rfcomm0: Device or resource busy
```The same feedback when trying to use minicom - "minicom: cannot open /dev/rfcomm0: Device or resource busy".

[/FONT][/COLOR][COLOR=#000000][FONT=Sans]When I run "**sudo** wvdial --config=phone.conf" everything is OK - connection established successfully. Bluetooth connection is still established by ordinary user, without sudo access. Also, nothing is blocked for ordinary user when I'm using same configurations and devices are connected via USB - the same mobile phone, or external USB  COM port.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Sans]Strace logs one may see for
"wvdial" (see line 174 and 177) at [/FONT][/COLOR][http://pastebin.com/PJvXTVby](http://pastebin.com/PJvXTVby)
[COLOR=#000000][FONT=Sans] "sudo wvdial" (see line 174) at [/FONT][/COLOR][http://pastebin.com/wa8p3hGW](http://pastebin.com/wa8p3hGW)[COLOR=#000000][FONT=Sans]

What is the mechanics? How to tune it?[/FONT][/COLOR]

---

### Post by Artif on 2012-07-04
Any ideas?

---

