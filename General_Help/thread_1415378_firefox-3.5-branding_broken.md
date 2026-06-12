---
title: "firefox-3.5-branding broken"
date: 2010-02-24
forum: General Help
---

### Post by Daremo_06 on 2010-02-24
I am having an issue with the latest firefox-3.5 update and I also have a broken dependancy for firefox-3.5 branding.  When I attempt to install the update via update manager it fails and I get the following.

> E: /var/cache/apt/archives/firefox-3.5_3.5.8+build1+nobinonly-0ubuntu0.9.10.1_i386.deb: trying to overwrite '/usr/bin/firefox', which is also in package firefox-mozilla-build 0


In Synaptic, Firefox-3.5-branding shows as a broken dependancy.  Under the dependancies details tab, I show the following conflicts

abrowser-3.5-branding
firefox-3.0-branding (<3.1~)
firefox-3.1-branding (<3.1~b4~hg20090317)

One other detail is that I have previously installed FF 3.6 via Ubuntuzilla, so I imagine what is going on is that its trying to update software thats newer than the update?

Lastly, I have tried running fix broken packages and it only changes the status color to green (installed) yet I still have the broken packages notification.

Any suggestions?

Thanks!

---

### Post by nanotube on 2010-02-25
the firefox-mozilla-build package from ubuntuzilla diverts the /usr/bin/firefox from the official package to /usr/bin/firefox.ubuntu, so the clash shouldn't be there.

have you by any chance fiddled with diverts? what's your output of ```
dpkg-divert --list
```

which versions of firefox do you currently have installed?

---

### Post by gmargo on 2010-02-25
I had a similar problem but solved it by removing the old firefox first, then installing the new one.

---

### Post by Daremo_06 on 2010-02-25
Divert listing is

> rob@rob-desktop:~$ dpkg-divert --list
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/share/dbus-1/services/org.freedesktop.Notifications.service to /usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd by notify-osd
diversion of /usr/bin/screen to /usr/bin/screen.real by screen-profiles
local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu
local diversion of /usr/bin/mozilla-firefox to /usr/bin/mozilla-firefox.ubuntu
diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185
diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-185
diversion of /usr/lib/xorg/modules/extensions/libglx.so to /usr/lib/nvidia/libglx.so.xserver-xorg-core by nvidia-glx-185
diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-185


Interesting.. When i go to the ubuntu software center and look at installed software, this is the version it says I have installed for FF.

> Version: 3.5.8+build1+nobinonly-0ubuntu0.9.10.1 (firefox-3.5-branding)

But when I select help from FF, I get version 3.6

I also see the following in synaptic

> firefox-3.5 (upgradeable)
firefox-3.5 (the broken package)
firefox-mozilla-build (has 0 kb interestingly enough...)

How can I list what packages I have installed.  I figure its a variant of ```
dpkg-query -W
```, but when I run that, I get a massive list that outruns the buffer in the shell so I only have the last part of the list.  In dos, I would have simply put a /p to pause each screenful of info.  How would I duplicate that in dpkg or have dpkg search just for firefox related packages?  I tried ```
dpgk-query -W "firefox"
``` and that didn't work.

Thanks!

---

### Post by gmargo on 2010-02-25
> **Daremo_06 said:**
> 
How can I list what packages I have installed. 

This is what I do.  The COLUMNS environment variable is there since dpkg stupidly truncates descriptions based on it's perceived terminal width.
```

COLUMNS=200 dpkg -l > ~/dpkg-l

```

---

