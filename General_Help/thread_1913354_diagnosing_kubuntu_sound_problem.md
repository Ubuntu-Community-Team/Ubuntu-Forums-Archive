---
title: "diagnosing kubuntu sound problem?"
date: 2012-01-22
forum: General Help
---

### Post by princeofnam on 2012-01-22
I will oddly lose sound for Rhythmbox and Amarok at the beginning of my session.  Sometimes sound will altogether disappear for every application.  I installed kubuntu for the first time a week ago and the first few days worked perfectly actually.  I checked the output using "pa aux | grep pulseaudio", and checked to see if "ls /usr/lib*/gstreamer-*/libgstpulse.so" returned anything

this is from the first command:

sushi 9409 0.7 0.1 341120 7112 ? S<l 21:04 0:00 /usr/bin/pulseaudio --start --log-target=syslog
sushi 9424 0.0 0.0 94816 3040 ? S 21:04 0:00 /usr/lib/pulseaudio/pulse/gconf-helper
sushi 9846 0.0 0.0 14560 896 pts/1 S+ 21:05 0:00 grep --color=auto pulseaudio



the second command only returns

/usr/lib/gstreamer-0.10/libgstpulse.so


-----------------


anyway i'm pretty confused

---

