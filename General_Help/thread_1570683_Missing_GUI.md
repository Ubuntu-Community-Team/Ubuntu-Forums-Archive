---
title: "Missing GUI"
date: 2010-09-08
forum: General Help
---

### Post by Jemop430 on 2010-09-08
I just updated from Ubuntu 10.04 to 10.10 and it seems that it lost it's GUI. I turn on my computer and, after logging in through the command line, it just goes to the command line. Is there some way for me to start the GUI if it's there and just not starting or is there some way for me to download the gui? I'm a linux noob so everything will need to be explained. Thank you.

---

### Post by andrewthomas on 2010-09-08
startx

---

### Post by Jemop430 on 2010-09-08
I've tried that and it doesn't work, it gives a server error. does startx try to download from x.org? if so I think my network is blocking it.

---

### Post by sixthwheel on 2010-09-08
Can you copy and paste the output of startx?

---

### Post by Jemop430 on 2010-09-08
I'm on two different computers so I don't know how I would transfer it over, so I would have to manually type it all. Also I don't know how to scroll up to see the whole entry

---

### Post by Jemop430 on 2010-09-08
ok so skipping all the unnecessary stuff from startx here is what it says:
Markers: (--) probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

(==) Log file:"/var/log/Xorg.0.log", Time: Wed Sep 8 17:14:36 2010
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) open /dev/fb0: No such fire or directory
(EE) intel (0): no kernel modesetting driver detected.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
          at [http://wiki.x.org](http://wiki.x.org)
 for help
Please also check the log file at "/var/log/Xorg.0.log" for additional information

  ddxSigGiveUp: Closing log
giving up
xinit: no such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno3): server error.

---

