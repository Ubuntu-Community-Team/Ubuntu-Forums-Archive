---
title: "I need a little troubleshooting guidance (Random freezes)"
date: 2010-01-20
forum: General Help
---

### Post by andrewkk on 2010-01-20
My Ubuntu 9.10 system freezes after being left on for several hours, and I can't figure out why.

Here are logs leading up to the point at which the system froze:
[LIST]
[*][daemon.log]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/daemon.log")
[*][kern.log]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/kern.log")
[*][messages]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/messages")
[*][syslog]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/syslog")
[*][Xorg.0.log]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/Xorg.0.log")
[/LIST]
Troubleshooting details:
[LIST]
[*]The system seems to freeze after approximately 1-4 hours of idle time, but I haven't measured this to be certain.
[*]The freeze usually happens while the "Blank screen" screen saver is on, so the most common symptom is the apparent inability to resume from the screen saver.
[*]The freeze has occasionally occurred while I was using the computer. When this happened, the mouse and keyboard stopped responding and the clock did not change.
[*]Disabling Compiz did not resolve the issue.
[*]I cannot try REISUB during a freeze, as this does nothing even when my system is not frozen.
[*]I don't know whether the keyboard LEDs change while in the frozen state. My keyboard does not have any LEDs.
[/LIST]

What else should I look at to try to find out what is causing this?

---

### Post by furry_freak on 2010-01-20
There doesn't appear to be anything unusual in the logs... Have you got your machine set to hibernate or anything?

---

### Post by andrewkk on 2010-01-20
It's not set to sleep or hibernate. I tested *xset dpms force off* and *sudo pm-suspend* just in case, and they both appear to be working.

---

### Post by wkulecz on 2010-01-20
Turn off all screen savers including blank screen and in the the power management display options set to always on, disable all other power management.  If the issues go away you can slowly enable what you've turned off, one at a time to get an idea of the buggy subsystem.

Other than that, boot into the memory test and see if it finds issues, if it doesn't or it crashes, make sure all fans are working and heatsinks attached, then try swapping in a known good power supply.

HTH,
--wally.

---

### Post by andrewkk on 2010-01-21
Thanks. I turned off the screen saver, and made sure that the power management preferences were to never put the computer to sleep and never put the display to sleep – but the system still froze after a few hours.

I also kept a log of thermal sensors. Here is the sensors output about 30 seconds before a freeze:
[LIST]
[*][sensors]("http://dl.dropbox.com/u/3296856/ubuntu-freeze_2010-01-20/sensors")
[/LIST]

---

### Post by andrewkk on 2010-05-16
I finally discovered that the freezes only occur when my PCI wireless card is plugged in. Switching from the ath5k to ath_pci driver "solved" the problem for me.

---

