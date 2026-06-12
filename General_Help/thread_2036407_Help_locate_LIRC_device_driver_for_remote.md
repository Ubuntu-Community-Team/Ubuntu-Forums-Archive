---
title: "Help locate LIRC device driver for remote"
date: 2012-08-01
forum: General Help
---

### Post by Bucky Ball on 2012-08-01
Hi all,

As the title suggests. I seem to have LIRC not properly installed as I was getting an error to that effect last night (will try to replicate with a fresh morning brain). I never got any configuration menu or options when I installed. 

But, when I plug my EZCap 646 USB DVB-T TV tuner into my Ubuntu 10.04 LTS hybrid running Xfce, and run dmesg, this is at the end (the TV tuner is before this and installed and working fine and using Me-TV and Xine now and then (slightly better picture for some reason)):

```
[  552.885161] IR Sony protocol handler initialized
[  552.890472] usbcore: registered new interface driver dvb_usb_rtl2832u
[  552.909339]** lirc_dev: IR Remote Control driver registered, major 250 **
[  552.913963]** IR LIRC bridge handler initialized**

```From the lines in bold a driver's being registered. 

**My Questions: **
1/ Where can I find where that registered driver is installed and what it is?

2/ How do I go about getting an auto-config of the remote (I press buttons, lirc figures it out!)?

3/ Related to Question #2; should I reinstall lirc as didn't get any conf setup at install? The remote apparently works with Win Media Centre (haven't tried but TV dongle is working in Win7 and XP also so I should; might get some more clues) so figure it will probably work if I configure as an 'MCE' device. If anyone already has that config file ... :)

I have a attached what I currently have in /etc/lirc/lircd.conf. I haven't tweaked it, that's lirc's default I guess. Any thoughts appreciated. Tnx in advance ... ;)

---

