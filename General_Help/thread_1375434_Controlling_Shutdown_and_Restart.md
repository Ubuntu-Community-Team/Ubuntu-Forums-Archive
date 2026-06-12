---
title: "Controlling Shutdown and Restart"
date: 2010-01-07
forum: General Help
---

### Post by dulac on 2010-01-07
hey guys, i tried looking but nothing specific showed up.

I know there is a way to shutdown the computer via command line and etc.

You can delay the shutdown time and things as such also. I was wondering, if there was a way to delay the reboot.

Say i shutdown now, i want to have it automatically reboot in an hour.

Is this something realistic?

Thanks in advance.

---

### Post by adoomer on 2010-01-08
I was just looking for an easy way to perform system shutdown and reboot on certain time and through Software Center I found quite useful and simple tool - GShutdown. If you don't have to do reboot through command line, it'll be good enough.

Although, I don't really know if it is possible to schedule boot so that it would work after shutdown.

---

### Post by garvinrick4 on 2010-01-08
Terminal:
Code:
sudo shutdown -r  "# minutes"     without quotes for reboot. Replace -r with -h for shutdown.

If want to reboot or shutdown replace minutes with "now"  without quotes.

---

### Post by garryknight on 2010-01-08
OP wants to shut down then reboot in an hour's time. This would require extra hardware: a timer plug, to be precise.

---

