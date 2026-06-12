---
title: "when I upgrade kubuntu 10.04 to 10.10,then boot is slow"
date: 2010-12-20
forum: General Help
---

### Post by maxwux on 2010-12-20
I recently upgraded kubuntu from 10.04 to 10.10
Slower boot time
First,systen will wait a few seconds on tty1
after a few seconds then jump to the login screen
Then wait for a few seconds to type
When I waiting the hard drive do not do anything

My hardware is lenovo r400
Intel (R) Core (TM) 2 Duo CPU P8700@2.53GHz
RAM 4G
Before the upgrade are quite fast boot
Become like this after the upgrade

It's my dmesg
[http://paste.plurk.com/show/340159/](http://paste.plurk.com/show/340159/)

[ 11.227578] type=1400 audit(1292894837.697:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=744 comm="apparmor_parser"
[ 30.947670] type=1400 audit(1292894857.417:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=974 comm="apparmor_parser"

11 second run /usr/lib/connman/scripts/dhclient-script
wait to 30 second do next??
and I can not find /usr/lib/connman/
anybody know what is this??

---

### Post by maxwux on 2010-12-21
any idea??

---

### Post by Zorael on 2010-12-21
That looks like a proper bug, so I'd suggest you head over to [Launchpad](http://launchpad.net/ubuntu) and file a bug report.

Remember, unreported bugs can only be fixed by accident.

---

### Post by maxwux on 2010-12-21
thanks
I will report

---

### Post by waynefoutz on 2010-12-21
I had a similar experience on my main laptop and Ubuntu. It booted up to a blank desktop with a cursor fast enough, but it took a good 45 seconds to a minute before the Gnome panels would appear. Went back to Lucid.

---

