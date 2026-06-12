---
title: "WinTV-HVR-950Q hybrid TV stick"
date: 2010-02-11
forum: General Help
---

### Post by rflores2323 on 2010-02-11
ok I bought this tv tuner.  I cannot get it to work however.

can anyone help me get this set up.  here is my dmesg log

[http://pastebin.ca/1794108](http://pastebin.ca/1794108)

I have read this post at [TV linux]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950Q")  and it says that it should work out the box with karmic,  my kernel is 2.6.31-17-generic

I scanned channels using this command tvtime-scanner and it found some channels here is the output

it shows channels picking up

```
xbmc@xbmc-desktop:~$ tvtime-scanner
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/xbmc/.tvtime/tvtime.xml
Scanning using TV standard NTSC.
Scanning from  44.00 MHz to 958.00 MHz.
Found a channel at 176.50 MHz (176.25 - 176.50 MHz), adding to channel list.
Found a channel at 184.00 MHz (183.75 - 184.00 MHz), adding to channel list.
Found a channel at 212.00 MHz (211.75 - 212.00 MHz), adding to channel list.
Found a channel at 511.75 MHz (511.50 - 511.75 MHz), adding to channel list.
Found a channel at 514.50 MHz (514.25 - 514.50 MHz), adding to channel list.
Found a channel at 538.00 MHz (537.75 - 538.00 MHz), adding to channel list.
Found a channel at 614.25 MHz (614.00 - 614.25 MHz), adding to channel list.
Found a channel at 731.00 MHz (730.75 - 731.00 MHz), adding to channel list.
Found a channel at 766.25 MHz (766.00 - 766.25 MHz), adding to channel list.
Found a channel at 794.25 MHz (794.00 - 794.25 MHz), adding to channel list.
Found a channel at 852.25 MHz (852.00 - 852.25 MHz), adding to channel list.
Found a channel at 867.00 MHz (866.50 - 867.50 MHz), adding to channel list.
Found a channel at 868.00 MHz (867.75 - 868.00 MHz), adding to channel list.
Found a channel at 881.50 MHz (881.25 - 881.50 MHz), adding to channel list.
Found a channel at 929.25 MHz (929.00 - 929.25 MHz), adding to channel list.
Found a channel at 932.50 MHz (932.25 - 932.50 MHz), adding to channel list.
Found a channel at 939.00 MHz (938.75 - 939.00 MHz), adding to channel list.
Found a channel at 939.75 MHz (939.50 - 939.75 MHz), adding to channel list.
xbmc@xbmc-desktop:~$  - No signal  
```

how do I configure tv time to work? it just comes up with a no signal

[IMG]http://www.ubuntu-pics.de/bild/42244/screenshot_002_jl6fVF.png[/IMG]
after I get this working I want to get the tvheadend working from this [XBMC Thread]("http://forum.xbmc.org/showthread.php?t=51945")

Pls help as I need help on this.

---

