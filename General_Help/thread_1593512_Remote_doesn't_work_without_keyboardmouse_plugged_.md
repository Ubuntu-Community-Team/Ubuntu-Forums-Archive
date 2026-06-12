---
title: "Remote doesn't work without keyboard/mouse plugged in"
date: 2010-10-11
forum: General Help
---

### Post by igoddard on 2010-10-11
I (finally!) have Mythtv working under 10.04.  I use the Haupaugge DVB-T card with its remote.  Whilst setting up the kit this worked OK.  When I unplugged the keyboard and mouse the system prior to installing it next to the TV appeared to have stopped responding to the remote.  In fact it seems to be responding to a number of the remote keys but not the OK and Go keys which isn't enough to run Mythtv.

I don't think leaving a keyboard & mouse plugged in is going to be domestically acceptable.

Does anyone have any ideas as to how to restore lirc functionality?

---

### Post by igoddard on 2010-10-11
It doesn't take much to fool it.  I plugged in a KVM switch.  Even without a keyboard or mouse plugged in it now works OK and /var/log/messages contains the lines

input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input4

which are present if the peripherals are plugged in but not when they're missing.

---

