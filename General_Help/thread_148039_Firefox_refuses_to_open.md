---
title: "Firefox refuses to open?"
date: 2006-03-21
forum: General Help
---

### Post by babygigi on 2006-03-21
Basically it just doesnt' open... i tried re-installing it with no luck... does anybody have any idea y it isn't working or hwo to fix it?

---

### Post by dermotti on 2006-03-21
try typing** firefox **from command line and see if you get errors. You could also download epiphany and try that.

---

### Post by gnu2tux on 2006-03-21
I take it you have actually tried restarting your pc or checking that it's not stuck in the process list somewhere.

(eg : ps axu|grep -i firefox)

Al.

---

### Post by babygigi on 2006-03-21
i just keep on getting this if i type it in terminal 

/opt/firefox/run-mozilla.sh: line 131: 14750 Segmentation fault      "$prog" ${1+"$@"}

---

### Post by MJSOnline on 2006-03-21
Hi.  Have you tried reinstalling firefox from Synaptic Package Manager as a ***last*** resort? Matthew

---

### Post by babygigi on 2006-03-21
Yeah i've tried that, from apt-get in terminal, the firefox site and from autopackage.org...

---

### Post by MJSOnline on 2006-03-21
Ok... Try removing all the firefox plugins from your system using Synaptic, reboot and try to reinstall firefox again. Matt

---

### Post by babygigi on 2006-03-21
okay gonna try that now hope it works :KS

---

### Post by babygigi on 2006-03-21
Nope... unfortunately that still doesn't not work....

---

### Post by towsonu2003 on 2006-03-21
[QUOTE=babygigi]i tried re-installing it with no luck...[/QUOTE]
from your error message, I see you have firefox 1.5 in breezy. did you remove firefox according to the wiki instructions (that is, if you used wiki)? Here is the pointer: [https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c](https://wiki.ubuntu.com/FirefoxNewVersion#head-51054869b8a40ea50859b0163c806e76f882499c)

These two parts are important:
-Close firefox...
```
# First, /usr/bin/firefox
 sudo rm /usr/bin/firefox
 sudo dpkg-divert --rename --remove /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo rm /usr/bin/mozilla-firefox
 sudo dpkg-divert --rename --remove /usr/bin/mozilla-firefox

```
and ```

rm -rf /opt/firefox
```

Move your profile to somewhere else (mv ~/.mozilla/firefox ~/.mozilla/firefox15.backup). Reinstall following the same wiki. 

Before doing all this, try starting with firefox --safe-mode
If that works, just close firefox and move your profile -> start firefox.

---

