---
title: "Atheros Zydas Ubuntu-Studio Upgrade Kernel Driver 64 bit"
date: 2011-04-06
forum: General Help
---

### Post by piroma on 2011-04-06
[FONT=Century Gothic][SIZE=2][COLOR=Black]Hi mates, I have a problem with my **wireless** device, it is about the famous (better said infamous) **Atheros Zydas driver zd1211rw**.
*I have just installed **Ubuntu studio**, as I had bought a midi controller and I wasn't feeling like installing a lot of programs. Default **kernel** with it "2.6.35-22-generic" and I'm using **64 bits version**.*
And the problem is that when I **upgrade** kernel to the last version, wireless stops working, and I don't know how to get to run the whole wireless system again.
I don't know how to **compile** the 64 bits driver, I don't even know how to get the right **source** of the driver
By the way I can't neither understand what is the diference between **madwifi and ath5k**, and how to make them run
What means to **load a module**?
**Modprobe** loads and unloads a module?
Which modules should I get to activate in order to make wireless system and the device work? What is atl2?
Do I have to recompile everything that deals with the wireless system? How?

I have tried to solve this problem by myself and I just messed all the kernel up...
That's why I have reinstalled so that I can even write this message. I need to upgrade kernel, an up-to-date system is essential.
**[COLOR=DarkRed]PLEASE[/COLOR] mates, lend me a hand.**[/COLOR][/SIZE][/FONT][FONT=Century Gothic]
                          [COLOR=DarkSlateBlue]*Piroma, from Spain.*[/COLOR]
[/FONT]
lshw information:
Wireless interface
/1
bus info: usb@1:2
logical name: wlan0
serial: 00:21:27:cc:b7:28
capabilities:
    ethernet,
    Physical interface,
    Wireless-LAN
configuration:
    broadcast: yes
    driver: zd1211rw
    driverversion: 2.6.35-22-generic
    firmware: N/A
    ip: 192.168.1.34
    link: yes
    multicast: yes
    wireless: IEEE 802.11bg

Aditional information on system by lshw
[http://piroma.jimdo.com/](http://piroma.jimdo.com/)

---

### Post by orestis46 on 2012-01-03
I had to update using the following link in Ubuntu 11.10 x64 for ZyDas1211 to work:

svn co [https://zd1211.svn.sourceforge.net/svnroot/zd1211](https://zd1211.svn.sourceforge.net/svnroot/zd1211) zd1211

---

