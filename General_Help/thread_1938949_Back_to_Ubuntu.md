---
title: "Back to Ubuntu"
date: 2012-03-10
forum: General Help
---

### Post by teddy379 on 2012-03-10
It's been a while since I used any Linux distros but yea, I'm giving Wine another try since I'm a gamer :)
So yea, I'm making this thread due to some issues I had after installing 11.10.
My internet is terrible and slower than in Windows7. It even stops responding at some point. When it happens I try to ping google or yahoo and my router's IP, None of those respond. I have the IPv6 on "Ignore".
Also, is there a widget sort of thing that I can have right at the toolbar beside the clock that can tell my current download and upload speed?

Thanks :)

EDIT: Do I need to install my Realtek LAN driver? If so, where do I get it from? I never had to download any drivers when I used Ubuntu about a year ago (10.xx)

---

### Post by teddy379 on 2012-03-11
bump

---

### Post by 2F4U on 2012-03-11
I think you would get better response if you would provide more details about the problem.
1. How do you connect (wireless, wired)?
2. How does your setup look like (router, modem, other PC's or laptops, dhcp/static IP)?
3. Details about your hardware specs

---

### Post by teddy379 on 2012-03-11
1. Wired
2. A router. I do have another PC connected to the router. I don't have a static IP.
3. My hardware, i5 2500K, PH67A-D3-B3 Gigabyte Mobo. GTX 560 Ti. 4 GB RAM.

After searching, it seems that I need to install the driver for my built in LAN.

EDIT:
This is what I found.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2)
This is my LAN chipset. I downloaded the first file in the Unix section. I'm not sure if it'd work since it supports an older kernel. I don't know though how to install it (it's a tar.bz2). I tried double clicking the makefile, the readme, and the autorun.sh but I don't know what happened.

---

### Post by llamabr on 2012-03-11
[http://ubuntuforums.org/showthread.php?t=1903016](http://ubuntuforums.org/showthread.php?t=1903016)

---

### Post by teddy379 on 2012-03-11
Okay. This is the output I got int the terminal. Does that mean it was installed? I still notice that the internet is slower than Windows.

```
tarique@tarique-PH67A-D3-B3:~$ cd /home/tarique
tarique@tarique-PH67A-D3-B3:~$ tar vjxf r8168-8.023.00.tar.bz2
r8168-8.023.00/
r8168-8.023.00/Makefile
r8168-8.023.00/src/
r8168-8.023.00/src/Makefile
r8168-8.023.00/src/r8168_asf.h
r8168-8.023.00/src/rtl_eeprom.c
r8168-8.023.00/src/r8168.h
r8168-8.023.00/src/r8168_n.c
r8168-8.023.00/src/r8168_asf.c
r8168-8.023.00/src/rtl_eeprom.h
r8168-8.023.00/src/rtltool.h
r8168-8.023.00/src/rtltool.c
r8168-8.023.00/src/Makefile_linux24x
r8168-8.023.00/README
r8168-8.023.00/autorun.sh
tarique@tarique-PH67A-D3-B3:~$ tar vjxf r8168-8.023.00.tar.bz2
r8168-8.023.00/
r8168-8.023.00/Makefile
r8168-8.023.00/src/
r8168-8.023.00/src/Makefile
r8168-8.023.00/src/r8168_asf.h
r8168-8.023.00/src/rtl_eeprom.c
r8168-8.023.00/src/r8168.h
r8168-8.023.00/src/r8168_n.c
r8168-8.023.00/src/r8168_asf.c
r8168-8.023.00/src/rtl_eeprom.h
r8168-8.023.00/src/rtltool.h
r8168-8.023.00/src/rtltool.c
r8168-8.023.00/src/Makefile_linux24x
r8168-8.023.00/README
r8168-8.023.00/autorun.sh
tarique@tarique-PH67A-D3-B3:~$ cd /home/tarique/r8168-8.023.00
tarique@tarique-PH67A-D3-B3:~/r8168-8.023.00$ sudo autorun.sh
[sudo] password for tarique: 
sudo: autorun.sh: command not found
tarique@tarique-PH67A-D3-B3:~/r8168-8.023.00$ sudo ./autorun.sh

Check old driver and unload it.
rmmod r8169
Build the module and install
[: 48: r8168: unexpected operator
Backup r8169.ko
rename r8169.ko to r8169.bak
Depending module. Please wait.
load module r8168
FATAL: Module r8168 not found.
Completed.

```

I really need a fix for this since I can't download anything atm unless it gets interrupted.

---

