---
title: "GStreamer was unable to detect any sound devices"
date: 2011-09-02
forum: General Help
---

### Post by wandalalakers on 2011-09-02
This is happening on a Gateway laptop.  Any help is appreciated.  I'm installing this on a laptop that had windows for a teen.  He is loving linux on another computer I installed it on by the way.
I currently have the modem disabled in setup.  The reason being is that with the modem enabled it thinks the modem is the sound card


aplay -l
device_list:235: no soundcards found...

lspci -v
ess technology es1988 allegro-1 (rev 12)
subsystem: gateway 2000 device 0401
flags: medium devsel, irq 5
i/o ports at 3800 [size=256]
capabilities: <access denied>


when doing the command as root I get:
ess technology es1988 allegro-1 (rev 12)
subsystem: gateway 2000 device 0401
flags: medium devsel, irq 5
i/o ports at 3800 [size=256]
capabilities: [c0] power management version 2

I found this thread and I'm trying this.
[http://ubuntuforums.org/showthread.php?t=64100](http://ubuntuforums.org/showthread.php?t=64100)
Open a terminal and type > sudo modprobe snd-maestro3

If no errors are spit back at you it has probably loaded the card. You may have to play around with some of the sound settings to get it to work. If problems do a search on sound, there are lots of threads.

If it works add: snd-maestro3 to /etc/modules with your favorite text editor. This will make it work from boot-up.

I didn't get an error when typing on sudo  modprobe snd-maestro3 but when I run the mixer, I still get the gstreamer was unable to detect any sound devices.

---

