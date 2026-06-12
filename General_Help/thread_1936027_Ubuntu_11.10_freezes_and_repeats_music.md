---
title: "Ubuntu 11.10 freezes and repeats music"
date: 2012-03-05
forum: General Help
---

### Post by npluis on 2012-03-05
A few times a day my machine freezes and it will repeat the last 3 seconds of sound it made. So if I play music I hear the last few seconds of that music repeating over and over again. Today I got an email in when it froze and if also repeated that sound.

It only seems to happen if I move my mouse. I have never seen it happen when I type something or when I do nothing. I did buy a new mouse but that hasn't helped. The only way to get out of the freeze is by restarting the machine.

Can someone please advise me where to look to diagnose this?

uname -a:
Linux Kermit 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux

Thanks

---

### Post by hwttdz on 2012-03-05
One good thing about this sort of freeze is that you know exactly when it happened (assuming you can see a clock on your desktop, with seconds is even better).  Before rebooting take note of the exact time displayed on the clock, which should have stopped when the computer froze.  

After rebooting go into /var/log and look at syslog and kern.log and Xorg.(most recent, I believe 0.log).  And pay special attention to the 1 minute leading up to the crash.  Hopefully you'll get a note about an exception or segfault in one program or another which might give us an idea where the issue is.

---

### Post by npluis on 2012-03-05
Thanks for your answer, I'll await the next freeze and check those logs. One question about the Xorg.0.log, there aren't any real times in there just something like [  9424.491], can I make a time from those numbers?

---

### Post by hwttdz on 2012-03-05
Xorg should reset to zero at restart, so it should still be fairly obvious when the crash happened.

---

### Post by npluis on 2012-03-09
Ok, here is syslog:
```
Mar  9 18:11:16 Kermit dhclient: DHCPREQUEST of 192.168.1.14 on eth0 to 192.168.1.1 port 67
Mar  9 18:11:16 Kermit dhclient: DHCPACK of 192.168.1.14 from 192.168.1.1
Mar  9 18:11:16 Kermit dhclient: bound to 192.168.1.14 -- renewal in 1439 seconds.
Mar  9 18:17:02 Kermit CRON[8434]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar  9 18:20:01 Kermit CRON[8454]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Mar  9 18:24:43 Kermit dhclient: DHCPREQUEST of 192.168.1.14 on eth0 to 192.168.1.1 port 67
Mar  9 18:24:43 Kermit dhclient: DHCPACK of 192.168.1.14 from 192.168.1.1
Mar  9 18:24:43 Kermit dhclient: bound to 192.168.1.14 -- renewal in 1782 seconds.
```kern.log:
```
Mar  9 17:25:47 Kermit kernel: [35443.404823] usb 8-1.2: USB disconnect, device number 9
Mar  9 17:25:48 Kermit kernel: [35444.133841] usb 8-1.2: new low speed USB device number 10 using uhci_hcd
Mar  9 17:25:48 Kermit kernel: [35444.338884] input: Microsoft Comfort Mouse 3000 as /devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.2/8-1.2:1.0/input/input5
Mar  9 17:25:48 Kermit kernel: [35444.339060] generic-usb 0003:045E:077B.0004: input,hidraw0: USB HID v1.11 Mouse [Microsoft Comfort Mouse 3000] on usb-0000:00:1d.2-1.2/input0
```Xorg.0.log:
```
[    44.663] (--) Microsoft Comfort Mouse 3000: Found relative axes
[    44.663] (--) Microsoft Comfort Mouse 3000: Found x and y relative axes
[    44.663] (--) Microsoft Comfort Mouse 3000: Found absolute axes
[    44.664] (II) evdev-grail: failed to open grail, no gesture support
[    44.664] (--) Microsoft Comfort Mouse 3000: Found keys
[    44.664] (II) Microsoft Comfort Mouse 3000: Configuring as mouse
[    44.664] (II) Microsoft Comfort Mouse 3000: Configuring as keyboard
[    44.664] (II) Microsoft Comfort Mouse 3000: Adding scrollwheel support
[    44.664] (**) Microsoft Comfort Mouse 3000: YAxisMapping: buttons 4 and 5
[    44.664] (**) Microsoft Comfort Mouse 3000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    44.664] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb8/8-1/8-1.2/8-1.2:1.0/input/input3/event3"
[    44.664] (II) XINPUT: Adding extended input device "Microsoft Comfort Mouse 3000" (type: KEYBOARD)
[    44.664] (**) Option "xkb_rules" "evdev"
[    44.664] (**) Option "xkb_model" "microsoftinet"
[    44.664] (**) Option "xkb_layout" "us"
[    44.664] (**) Option "xkb_options" "lv3:ralt_switch"
[    44.664] (II) Microsoft Comfort Mouse 3000: initialized for relative axes.
[    44.664] (WW) Microsoft Comfort Mouse 3000: ignoring absolute axes.
[    44.664] (**) Microsoft Comfort Mouse 3000: (accel) keeping acceleration scheme 1
[    44.664] (**) Microsoft Comfort Mouse 3000: (accel) acceleration profile 0
[    44.664] (**) Microsoft Comfort Mouse 3000: (accel) acceleration factor: 2.000
[    44.664] (**) Microsoft Comfort Mouse 3000: (accel) acceleration threshold: 4
[    44.664] (II) config/udev: Adding input device Microsoft Comfort Mouse 3000 (/dev/input/mouse0)
[    44.664] (II) No input driver/identifier specified (ignoring)
[    44.668] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    44.668] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    44.668] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    44.668] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    44.668] (**) AT Translated Set 2 keyboard: always reports core events
[    44.668] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    44.668] (--) AT Translated Set 2 keyboard: Found keys
[    44.668] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    44.668] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    44.668] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    44.668] (**) Option "xkb_rules" "evdev"
[    44.669] (**) Option "xkb_model" "microsoftinet"
[    44.669] (**) Option "xkb_layout" "us"
[    44.669] (**) Option "xkb_options" "lv3:ralt_switch"
[    66.146] (II) intel(0): EDID vendor "HWP", prod id 10273
[    66.146] (II) intel(0): Using hsync ranges from config file
[    66.146] (II) intel(0): Using vrefresh ranges from config file
[    66.146] (II) intel(0): Printing DDC gathered Modelines:
[    66.146] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    66.146] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    66.146] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    66.147] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    66.147] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    66.147] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    66.147] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    66.147] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    66.147] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    66.147] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    66.147] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    70.128] (II) intel(0): Allocated new frame buffer 3840x1080 stride 15360, tiled
[    70.414] (II) intel(0): EDID vendor "HWP", prod id 10273
[    70.415] (II) intel(0): Using hsync ranges from config file
[    70.415] (II) intel(0): Using vrefresh ranges from config file
[    70.415] (II) intel(0): Printing DDC gathered Modelines:
[    70.415] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    70.415] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    70.415] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    70.415] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    70.415] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.415] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    70.415] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    70.415] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    70.415] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    70.415] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    70.415] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    70.634] (II) intel(0): EDID vendor "HWP", prod id 10273
[    70.634] (II) intel(0): Using hsync ranges from config file
[    70.634] (II) intel(0): Using vrefresh ranges from config file
[    70.634] (II) intel(0): Printing DDC gathered Modelines:
[    70.634] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    70.634] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    70.634] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    70.635] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    70.635] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.635] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    70.635] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    70.635] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    70.635] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    70.635] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    70.635] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    70.983] (II) intel(0): EDID vendor "HWP", prod id 10273
[    70.983] (II) intel(0): Using hsync ranges from config file
[    70.983] (II) intel(0): Using vrefresh ranges from config file
[    70.983] (II) intel(0): Printing DDC gathered Modelines:
[    70.983] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[    70.983] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    70.983] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    70.983] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    70.983] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    70.983] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    70.983] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    70.983] (II) intel(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    70.983] (II) intel(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    70.983] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    70.983] (II) intel(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[    74.193] (II) XKB: reuse xkmfile /var/lib/xkb/server-FFB041D6465B5D8DDB77D3B692B07736DA4F05CB.xkm
```Now, the lines from kern.log are at least half an hour before it crashed. I told before it was mainly when I moved my mouse but the last two days it happened when I was away from my machine. When I look at the lines in Xorg.0.log I can see messages about my monitors (dual monitor setup) and I think it might have started when I attached the second monitor (but not sure). 

Can you see something wrong in these lines?

---

