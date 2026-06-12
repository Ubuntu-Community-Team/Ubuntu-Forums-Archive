---
title: "MultiSeat - No login and keyboard error"
date: 2011-01-30
forum: General Help
---

### Post by Jummel on 2011-01-30
I've been following the following guide for multiseat:
[https://help.ubuntu.com/community/MultiseatX]("https://help.ubuntu.com/community/MultiseatX")
 After much trial and tribulation, I got the machine to boot so both screens come up, with one mouse for each screen.
Problem is one screen (seat 1) doesn't show a login box, just the background image
Seat 0 displays the login box fine, logs in and works great.

I noticed the following error in my Xorg.0.log
[   113.080] (EE) Unable to open evdev device "/dev/input/by-path/pci-0000:00:13.1-usb-0:1.3:1.0-event-kbd".
[   113.080] (II) UnloadModule: "evdev"
[   113.080] (EE) PreInit returned NULL for "Keyboard0"
[   113.250] (EE) PreInit returned NULL for "Logitech USB Receiver"
I get much the same error in Xorg.1.log, for the second keyboard (another logitech)

I have an NVidia graphics card (seat 0) and an ATI (seat 1)
amd64, ubuntu 10.10

Attached are my Xorg.conf and kdmrc

Any Ideas?

---

### Post by Jummel on 2011-02-03
Solved it:
refer to [http://ubuntuforums.org/showthread.php?p=10423991#post10423991]("http://ubuntuforums.org/showthread.php?p=10423991#post10423991") for my configs if you need

---

