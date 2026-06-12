---
title: "Serial Port Problems"
date: 2011-02-02
forum: General Help
---

### Post by kngunn on 2011-02-02
This little problem is driving me nuts...

I have a piece of software (a script that communicates serially with a piece of home automation hardware) that works perfectly under 10.04 but has problems under 10.10.  I've tried upgrades AND clean installs, and I'm currently running both on the same computer via two different partitions.

If I run Minicom (set to use ttyS0), let it initialize /dev/ttyS0, and then exit (without "resetting the modem") and wait 30 seconds, the script runs fine afterwards. If I don't -- nothing.

I've looked at the various /etc/rcS.d files and can't find a difference.  I've looked at /var/lib/setserial/autoserial.conf and can't find a difference.  Permissions look fine on /dev/ttyS0 as well.

Bottom line, however, is that the port appears to be getting automatically initialized in 10.04 but not in 10.10.  I've tried adding setserial commands to rc.local, but that doesn't do the trick either.

Does ANYONE have ANY idea what I need to do?  Clearly, Minicom is doing something that initializes the port that the system isn't doing at boot -- and which 10.04 WAS doing at boot.  Any help you can offer will be greatly appreciated!

---

