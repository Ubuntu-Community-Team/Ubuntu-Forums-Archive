---
title: "Bash Scripts to run things only in KDE, or Gnome, etc"
date: 2009-12-24
forum: General Help
---

### Post by UltraZone on 2009-12-24
I have both Gnome and KDE installed.  I have several desktop eyecandy like Conky and Cairo-dock that I want to run only when I log in to Gnome, but when I log in to KDE I don't want them to be launched.  My question is, how do I include code in a bash script that will test what session has been logged on to, and launch or not launch the app?  Thx

---

### Post by niteshifter on 2009-12-24
Hi,

Check for the presence of environment variables unique to each DM:

```
#!/bin/bash
#
if test "${GDMSESSION+set}" == set ; then
 echo "GNOME in use"
fi
if test "${KDEDIR+set}" == set ; then
 echo "KDE in use"
fi

```

---

