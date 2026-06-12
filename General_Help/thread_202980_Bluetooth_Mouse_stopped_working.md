---
title: "Bluetooth Mouse stopped working"
date: 2006-06-24
forum: General Help
---

### Post by rinch on 2006-06-24
Hi,

my bluetooth mouse has stopped working.

As far as I can tell, the key info from the logs is:
> Jun 24 21:43:04 localhost hcid[6234]: Can't get system message bus name: Connection ":1.20" is not allowed to own the service "org.bluez" due to security policies in the configuration file

searching/scanning with hidd or hcitool finds no devices

The problem is not the hardware, which is working in Windows, and was working perfectly in Dapper when I last tried it.

I've made a few changes since then, including a kernel upgrade, but it seems like this shouldn't be the problem - especially if no-one else is reporting the same problem.

any ideas?  Please help! :o)

---

### Post by agblakey on 2006-07-20
did you get this working?  I am having the same problem, but only with my upgraded 2.6.17 kernel.  My mouse works fine with the Ubuntu 2.6.15-26 kernel on the same machine.  Boot one it works, boot the other it doesn't.  I got it to work with 2.6.15 by adding org.bluez to /etc/dbus-1/system.d/bluez.conf configuration file.

---

### Post by rinch on 2006-07-20
try this - [http://ubuntuforums.org/showthread.php?t=205319](http://ubuntuforums.org/showthread.php?t=205319)

which details most of what i did to get it working.

As you did, I think it's also necessary to add and entry for org.bluez to /etc/dbus-1/system.d/bluez.conf

---

