---
title: "NTP connected but still drifting"
date: 2011-12-20
forum: General Help
---

### Post by Rudibot on 2011-12-20
I have a laptop running 9.04.

The clock drifts about 1.6 seconds per day when left to its own devices. I can enable NTP but it seems to drift too!

Refering to the attached pic - you can see 0 offset when I boot up the laptop and the system clock syncs with the hardware clock. The hardware clock is quite stable. The system clock then proceeds to drift until I enable NTP at about 11:00. The NTP brings the offset in but then proceeds to drift the other way.

Any ideas would be great,
Data comes from ntp -q command.

---

### Post by Lars Noodén on 2011-12-20
Which package do you have installed, OpenNTP or NTP?  Is ntpd running?

---

### Post by Rudibot on 2011-12-20
ntp is installed. I have the ntpd daemon running becase I can query it for connected time servers. I enabled ntp via the Gnome Time and Date applet.

---

### Post by dcstar on 2011-12-21
> **Rudibot said:**
> I have a laptop running 9.04.

The clock drifts about 1.6 seconds per day when left to its own devices. I can enable NTP but it seems to drift too!
...........
Any ideas would be great,


[http://ubuntuforums.org/showthread.php?t=956263](http://ubuntuforums.org/showthread.php?t=956263)

---

### Post by Rudibot on 2011-12-21
Ok I'll enable this and retry the test.
The clock has actually stabilized a bit - it is now oscillating.

---

