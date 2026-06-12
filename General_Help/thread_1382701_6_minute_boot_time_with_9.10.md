---
title: "6 minute boot time with 9.10"
date: 2010-01-16
forum: General Help
---

### Post by elbows on 2010-01-16
I just installed Ubuntu 9.10 on an Athlon 1.4GHz wi/ 768M of RAM. Everything works fine except that it takes 6+ minutes to boot up. During most of that time, the screen is completely blank and there's no disk activity. If I Ctrl+Alt+F1 to a text console, I just see a blinking cursor.

Eventually the disk will start working and from that point on it boots pretty quickly.

Bootchart shows a brief spike in disk activity, then sh starts and the CPU hits 100% and stays there (chart attached).

dmesg shows this:
[FONT="Courier New"][    2.443613] usbcore: registered new interface driver usbhid
[    2.443621] usbhid: v2.6:USB HID core driver
[    3.605261] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000301b1d4c75]
[  345.052857] PM: Starting manual resume from disk
[  345.052872] PM: Resume from partition 8:5
[  345.052876] PM: Checking hibernation image.
[/FONT]

Notice the gap between 3s and 345s, where nothing at all seems to be happening.

Is there any way to figure out what sh is doing during all that time?

---

### Post by nullmind on 2010-01-16
Have you tried booting without the "quiet" option and disabling the splash screen to make sure you're getting the most verbose output?

You also might want to try disabling some startup services. I'm not pointing any fingers, but when I've seen this it was related to some kind of hardware glitch, such as the voltage on a USB bus being out of range. Sometimes it takes a while for the system to find out the hardware is faulty, or the "noise" being generated confuses the OS.

---

### Post by elbows on 2010-01-16
Huh. If I remove "splash" from the boot command, it boots in under 30 seconds.

I don't think the splash screen was working in the first place -- all I ever saw was a blank screen until the X server started. Besides, rapidly-scrolling text during bootup is comforting. :)

So I'll just leave it turned off and be happy.

---

### Post by john newbuntu on 2010-01-17
In case you want your splash back, read comment #39 in this forum:
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/61711](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/61711)

---

