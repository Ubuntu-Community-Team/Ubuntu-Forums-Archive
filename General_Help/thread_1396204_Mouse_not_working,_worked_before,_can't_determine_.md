---
title: "Mouse not working, worked before, can't determine cause. Possibly xorg.conf related."
date: 2010-02-01
forum: General Help
---

### Post by labrat256 on 2010-02-01
Hello


2 days ago, I was using my Toshiba Equium laptop with Ubuntu 9.10, and despite a few problems it was largely fine. However, it wouldn't shut down (it got to "shutting down alsa" and stopped, for at least 10 mins) so I hard rebooted it. When I booted it up, there was a mouse cursor, which wouldn't move. I'd not changed anything else that time.

A quick google told me to look in /etc/X11/xorg.conf for my mouse settings, upon opening that file, there were no mouse settings of any kind, so I surmised that something had removed them and I needed to get them back somehow. After reading many an FAQ about manually configuring xorg.conf, nothing seemed to work, including dpkg-reconfigure xserver-xorg.

So I booted up the 9.10 LiveCD, hoping that the mouse would work. It does! So, I went to attempt to copy the contents of xorg.conf into the one on my filesystem, but the LiveCD doesn't have one...

Any ideas??

---

### Post by NightwishFan on 2010-02-01
Ubuntu 9.10 does not need a Xorg.conf file (I believe). Mine is a minimal one that simply identifies my Nvidia driver. I am not sure if deleting or moving it would help. Perhaps temporarily rename Xorg.conf to Xorg.conf.backup and create a new empty file called Xorg.conf, and see if it works. If not, then just restore the backup one. Be careful working as root, and make sure the backup stays safe.

---

### Post by labrat256 on 2010-02-01
Ah, fair enough! What would anybody recommend then for diagnosing a mouse not working?

---

### Post by NightwishFan on 2010-02-01
Check the syslog messages when you insert the mouse. You can find the system log in System -> Administration -> Log File Viewer.

---

### Post by labrat256 on 2010-02-01
I'm sorry, I neglected to add that I'm trying to use the touchpad on my laptop. I don't have access to any mouse to test it, and it works perfectly in windows and using the LiveCD.

---

### Post by NightwishFan on 2010-02-01
Did you try my suggestion above?

---

### Post by labrat256 on 2010-02-02
I am unable to unplug, or insert the mouse. Is there any way to 'disconnect' the built in touch pad as far as the OS is concerned to get the log?

---

### Post by NightwishFan on 2010-02-02
I am unsure, you could also check the Xorg log for errors. Generally problems seem to jump out in them. If you need the keyboard to navigate, ALT+F1 opens the main menu.

---

### Post by labrat256 on 2010-02-02
Right, using the LiveCD seems to have spontaneously fixed it. Can't work out why, if I could, I'd know a hell of a lot more about Ubuntu/Linux!

For the record, the only log mention of the touchpad was in xorg.20.log and was:

> (II) Synaptics touchpad driver version 0.99.3
(**) Option "Device" "/dev/input/event7"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found

Which doesn't seem to say anything. Thanks for your help, and if anybody in the future has a similar issue, and wants my logs/anything, feel free to PM me.

---

