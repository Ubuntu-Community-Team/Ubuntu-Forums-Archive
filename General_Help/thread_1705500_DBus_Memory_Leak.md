---
title: "DBus Memory Leak"
date: 2011-03-12
forum: General Help
---

### Post by laserbeam on 2011-03-12
For some time now, (months, I think), I've been having memory hangs, which mostly spin around dbus-deamon. As far as I learned from other posts and google, dbus starts filling up memory when some other program floods it with messages or something like that (correct me if I am wrong please.)

I figured out today that clementine was clogging up dbus (when clementine is on and running, dbus fills up about 0.05 - 0.1 MB of RAM per second).

Right now, I am at 2 hrs of uptime with dbus-deamon looks like this in a ```
ps aux
``` listing:
catalin   1656  1.0  6.6 161576 128392 ?       Ss   14:23   1:15 /bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session

If I stop clementine, memory usage still climbs (though much slower), something else must be hanging it as well.

Can someone explain me how dbus processes messages (or whatever is sent to it)? What happens when it can not process something? Is there any way to clear all the messages stuck in it's queue? (I know nothing of how dbus works internally).

Some other sites suggested I use ```
dbus-monitor --session
``` to figure out what is wrong. A couple seconds of this running can be found [here]("http://pastebin.ubuntu.com/579279/") (clementine was closed), however I can't really make heads or tails about that. It doesn't really show anything else (at least not now), but memory usage still goes up.

I really don't know what to do about this, and I appreciate any help.

Thanks.

---

### Post by jago25_98 on 2011-05-27
I have the same problem. 
Your post is the only recent post on the matter, other date back a few years to 2009 and other distributions. 

However, I also had problems with keyboard detection & upstart after an upgrade. Did you have these problems? 

I fixed the keyboard problem by chroot'ing in and running *dpkg-reconfigure -a*. I now have what appears to be a working system but I still get a memory leak from running /etc/init.d/dbus start

Subscribing to thread.

found this on another thread: "Dbus is now left behind on actual distro, replaced by udev

Dbus have links with: GLib, Python, Qt & Java. So you might have either some old settings breaking your system, or some weird app still using dbus"

---

