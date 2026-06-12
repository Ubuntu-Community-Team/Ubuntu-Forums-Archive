---
title: "Disable shutdown and restart dialogs?"
date: 2012-01-02
forum: General Help
---

### Post by josephellengar on 2012-01-02
11.10, gnome fallback.

Whenever I shutdown/restart, even from gnome-do, I get a dialog asking me if I am sure. (Yes, by the way) Or, when I want to restart, I have to select shutdown from the option and then click restart on the dialog that pops up. Is there any way to modify this behavior, add a shutdown option to the menu and/or disable the confirmation dialog? In Maverick I used gconf-editor, but I couldn't find those keys in the editor anymore in 11.10.

---

### Post by stinkeye on 2012-01-03
Have a look in dconf-editor.

eg in the terminal this will suppress the confirmation dialogue but then
in unity you loose the restart option because it only appears in 
the shutdown confirmation window.
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```


There's also this which doesn't work in unity but may work in the fallback session.
```
gsettings set org.gnome.SessionManager logout-prompt false
```

---

### Post by josephellengar on 2012-01-03
> **stinkeye said:**
> Have a look in dconf-editor.

eg in the terminal this will suppress the confirmation dialogue but then
in unity you loose the restart option because it only appears in 
the shutdown confirmation window.
```
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```


There's also this which doesn't work in unity but may work in the fallback session.
```
gsettings set org.gnome.SessionManager logout-prompt false
```

Thanks!

---

### Post by gfwilliams on 2012-04-13
Hi, I am running a fresh install of 11.10 (a minimal install from the alternate CD, followed by lightdm and gnome-fallback).

I have tried the following and I still get the suspend/hibernate/restart/cancel/shutdown window, when selecting 'Shut down', or even pressing the power button:

```
gsettings set org.gnome.settings-daemon.plugins.power button-power 'shutdown'
gsettings set org.gnome.SessionManager logout-prompt false
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

I found a (quite hacky) way to fix this was just to save the following to /etc/acpi/powerbtn.sh

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.
/sbin/shutdown -h now "Power button pressed"
```

Hope that helps somebody!

---

### Post by GreenRaccoon on 2012-06-09
> **gfwilliams said:**
> Hi, I am running a fresh install of 11.10 (a minimal install from the alternate CD, followed by lightdm and gnome-fallback).

I have tried the following and I still get the suspend/hibernate/restart/cancel/shutdown window, when selecting 'Shut down', or even pressing the power button:
```
gsettings set org.gnome.settings-daemon.plugins.power button-power 'shutdown'
gsettings set org.gnome.SessionManager logout-prompt false
gsettings set com.canonical.indicator.session suppress-logout-restart-shutdown true
```

I found a (quite hacky) way to fix this was just to save the following to /etc/acpi/powerbtn.sh

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.
/sbin/shutdown -h now "Power button pressed"
```

Hope that helps somebody!

Nice! Thanks! I've been looking everywhere for a solution to this. The solutions that I've used for Gnome 3 (Ubuntu 12.04) don't work for Cinnamon (Linux Mint 13). Just for reference, I'll paste the output of the default version of my "/etc/acpi/powerbtn.sh" file.

```
#!/bin/sh
# /etc/acpi/powerbtn.sh
# Initiates a shutdown when the power putton has been
# pressed.

[ -r /usr/share/acpi-support/power-funcs ] && . /usr/share/acpi-support/power-funcs

# getXuser gets the X user belonging to the display in $displaynum.
# If you want the foreground X user, use getXconsole!
getXuser() {
        user=`pinky -fw | awk '{ if ($2 == ":'$displaynum'" || $(NF) == ":'$displaynum'" ) { print $1; exit; } }'`
        if [ x"$user" = x"" ]; then
                startx=`pgrep -n startx`
                if [ x"$startx" != x"" ]; then
                        user=`ps -o user --no-headers $startx`
                fi
        fi
        if [ x"$user" != x"" ]; then
                userhome=`getent passwd $user | cut -d: -f6`
                export XAUTHORITY=$userhome/.Xauthority
        else
                export XAUTHORITY=""
        fi
        export XUSER=$user
}

# Skip if we just in the middle of resuming.
test -f /var/lock/acpisleep && exit 0

# If the current X console user is running a power management daemon that
# handles suspend/resume requests, let them handle policy This is effectively
# the same as 'acpi-support's '/usr/share/acpi-support/policy-funcs' file.

[ -r /usr/share/acpi-support/power-funcs ] && getXconsole
PMS="gnome-settings-daemon kpowersave xfce4-power-manager"
PMS="$PMS guidance-power-manager.py dalston-power-applet"

if pidof x $PMS > /dev/null; then
        exit
elif test "$XUSER" != "" && pidof dcopserver > /dev/null && test -x /usr/bin/dcop && /usr/bin/dcop --user $XUSER kded kded loadedModules | grep -q klaptopdaemon; then
        exit
elif test "$XUSER" != "" && test -x /usr/bin/qdbus; then
        kded4pid=$(pgrep -n -u $XUSER kded4)
        if test "$kded4pid" != ""; then
                dbusaddr=$(su - $XUSER -c "grep -z DBUS_SESSION_BUS_ADDRESS /proc/$kded4pid/environ")
                if test "$dbusaddr" != "" && su - $XUSER -c "export $dbusaddr; qdbus org.kde.kded" | grep -q powerdevil; then
                        exit
                fi
        fi
fi

# If all else failed, just initiate a plain shutdown.
/sbin/shutdown -h now "Power button pressed"
```
This file is from Linux Mint 13, but I'm guessing it'd be the same in Ubuntu 12.04.

If anyone wants to know the other solutions I found, there's this thread:
[http://forums.linuxmint.com/viewtopic.php?f=208&t=104602&p=591180#p591180]("http://forums.linuxmint.com/viewtopic.php?f=208&t=104602&p=591180#p591180")
The first one worked for Ubuntu 12.04 using Gnome 3.

---

