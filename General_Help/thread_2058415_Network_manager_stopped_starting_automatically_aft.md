---
title: "Network manager stopped starting automatically after boot"
date: 2012-09-15
forum: General Help
---

### Post by alek66 on 2012-09-15
Weird.... out of the blue, network manager stopped starting automatically.... 
Now after each boot I got to sudo service network-manager start....

What log can I see to get a hit of whats going on?

It seems as Lubuntu, is not so tidy.... I get a lot of random crashes... (I installed a stable edition)

---

### Post by marinara on 2012-09-16
someone in irc had this bug, somehow "managed' got turned off.  he turned it on, and rebooted and fixed

---

### Post by alek66 on 2012-09-16
> **marinara said:**
> someone in irc had this bug, somehow "managed' got turned off.  he turned it on, and rebooted and fixed

Marinara, thanks... "been there got the shirt" afeter several reboots still there.

Will keep investigating.

---

### Post by marinara on 2012-09-16
[http://ubuntuforums.org/showpost.php?p=6811689&postcount=2](http://ubuntuforums.org/showpost.php?p=6811689&postcount=2)
this post

---

### Post by varunendra on 2012-09-18
Post back the output of:
```
cat /etc/xdg/autostart/nm-applet.desktop
```

---

### Post by alek66 on 2012-09-18
> **varunendra said:**
> Post back the output of:
```
cat /etc/xdg/autostart/nm-applet.desktop
```

[Desktop Entry]
Name=Network
Comment=Manage your network connections
Icon=nm-device-wireless
Exec=nm-applet
Terminal=false
Type=Application
NoDisplay=true
NotShowIn=KDE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet

---

### Post by varunendra on 2012-09-18
Nothing is wrong there (same as mine). Please check your* ~/.config/autostart* directory to see if somehow a copy of the same file has been created there, and if its contents differ:
```
ls ~/.config/autostart/
```
If nm-applet.desktop file appears there, check and match its contents:
```
cat ~/.config/autostart/nm-applet.desktop
```

---

### Post by alek66 on 2012-09-18
> **varunendra said:**
> Nothing is wrong there (same as mine). Please check your* ~/.config/autostart* directory to see if somehow a copy of the same file has been created there, and if its contents differ:
```
ls ~/.config/autostart/
```
If nm-applet.desktop file appears there, check and match its contents:
```
cat ~/.config/autostart/nm-applet.desktop
```

Autostart:

> blueman.desktop  print-applet.desktop  tangerine.desktop  vino-server.desktop

tangerine, I purged it yesterday....

---

### Post by varunendra on 2012-09-19
I've no idea where else to look. Maybe it tries to autostart but something is causing it to crash during startup. If so, there must be some hint in the log files.

What if you add nm-applet manually to "Startup Applications"? Does it autostart then?

---

