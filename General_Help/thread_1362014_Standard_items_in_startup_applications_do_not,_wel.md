---
title: "Standard items in startup applications do not, well... startup"
date: 2009-12-22
forum: General Help
---

### Post by gspat on 2009-12-22
Hi!

I tried playing with Orca, didn't like it and turned it off again, but now certain items don't seem to startup when I boot-up or login...

ie:

nm-applet
gnome-volume-control-applet

sound still works and I still have network connectivity, but they don't show up in the notification area until I run them from a terminal window.

There may be others, but these two are the main ones I'm concerned about.

Running system monitor shows that most items ARE started and running.

I could write a script, but that seems counter productive!

---

### Post by dcstar on 2009-12-22
> **gspat said:**
> Hi!

I tried playing with Orca, didn't like it and turned it off again, but now certain items don't seem to startup when I boot-up or login...

ie:

nm-applet
gnome-volume-control-applet

sound still works and I still have network connectivity, but they don't show up in the notification area until I run them from a terminal window.

There may be others, but these two are the main ones I'm concerned about.

Running system monitor shows that most items ARE started and running.

I could write a script, but that seems counter productive!

System-Preferences-Startup Applications.

---

### Post by gspat on 2009-12-22
Yup... that's where I should be able to set them...

I apologize if I wasn't specific enough, but that's where I started from, and then used system manager to verify that most items listed in it were running.

If it helps, everything in it is checked and sound manager and network manager applets are listed there.

---

### Post by dcstar on 2009-12-22
> **gspat said:**
> Yup... that's where I should be able to set them...

I apologize if I wasn't specific enough, but that's where I started from, and then used system manager to verify that most items listed in it were running.

If it helps, everything in it is checked and sound manager and network manager applets are listed there.

Check their launcher settings, then disable and re-enable each of them.

---

### Post by 3rdalbum on 2009-12-22
At the login screen, after you type your username, make sure that the session is set to "GNOME" and not "GNOME (failsafe)".

The Failsafe Gnome session will not run your startup programs.

---

### Post by gspat on 2009-12-23
> Re: Standard items in startup applications do not, well... startup
At the login screen, after you type your username, make sure that the session is set to "GNOME" and not "GNOME (failsafe)".

The Failsafe Gnome session will not run your startup programs. 

I don't believe I running in failsafe mode... I'll check again once I've finished this post.

> **dcstar said:**
> Check their launcher settings, then disable and re-enable each of them.

ok.. I unchecked all items in the startup applications window and rebooted, then re-checked them all (except Evolution alarm notifier, login sound, Power Manager, remote desktop managment and screensaver)

still the same.

My apologies for the length of this post... I wanted to get it down on the forum for others to help me learn a bit more and (hopefully) get some feedback on it).

This is just a list I made comparing what is in startup  applications and what is in system monitor right after startup. I'll focus on the unknown and not started items from it.

```

list of startup apps             status
---------------------------------------------
AT SPI Registry Wrapper          Not Started
Bluetooth Applet                 Not Started
Check for new hardware drivers   Unknown
Disk Notifications               Unknown
Gnome Keyring Daemon             Started
Gnome Settings Daemon            Started
Gnome settings daemon helper     Unknown
Indicator Applet                 Started
Network Manager                  Not Started
PolicyKit Authentication Agent   Unknown
Print Queue Applet               Unknown
Seahorse Daemon                  Not Started
Update Notifier                  Unknown
User Folders Update              Unknown
Volume Control                   Not Started

```

This is the output from the terminal when I run the commands in startup applications from the terminal for the Not Started and Unknown programs:

**AT SPI Registry Wrapper:**

```
glen@glen-desktop:~$ /usr/lib/at-spi/at-spi-registryd &
[2] 2516
glen@glen-desktop:~$ 
** (<unknown>:2516): WARNING **: Could not set GTK_MODULES: Setenv interface is only available during the Initialization phase
** (<unknown>:2516): DEBUG: Client registered with session manager: /org/gnome/SessionManager/Client8
```

Shows up in system monitor.

**Bluetooth Applet:**

```
glen@glen-desktop:~$ bluetooth-applet &
[1] 2253
glen@glen-desktop:~$ ** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3glen@glen-desktop:~$ bluetooth-applet &
[1] 2253
glen@glen-desktop:~$ ** Message: Reading of RFKILL events failed
** Message: killswitches state 3
** Message: killswitches state 3
```

Bluetooth applet then shows up in system monitor, but presuambly not in the notification tray since there are no bluetooth devices.

**Check For New Hardware Drivers:**

```
glen@glen-desktop:~$ sh -c 'test -e /var/cache/jockey/check || exec jockey-gtk --check 60'&
[3] 2521
glen@glen-desktop~:$
```

My guess here is that it waits for 60 seconds and then does it's check and quits.

**Disk Notifications:**

```
glen@glen-desktop:~$ /usr/lib/gnome-disk-utility/gdu-notification-daemon &
[4] 2523
[3]   Done                    sh -c 'test -e /var/cache/jockey/check || exec jockey-gtk --check 60'
glen@glen-desktop:~$
```

**Gnome Settings Daemon Helper:**

```
glen@glen-desktop:~$ /usr/lib/gnome-session/helpers/gnome-settings-daemon-helper &
[5] 2525
glen@glen-desktop:~$ 
** (gnome-settings-daemon-helper:2525): WARNING **: Could not set GTK_RC_FILES: Setenv interface is only available during the Initialization phase
[5]+  Done                    /usr/lib/gnome-session/helpers/gnome-settings-daemon-helper
```

No idea... runs once during startup then is done and stops? IS this related to gnome-pty-helper?

**Network Manager:**

```
glen@glen-desktop:~$ nm-applet --sm-disable &
[5] 2526
glen@glen-desktop:~$
```

This seems to start the nm-applet just fine... a nice little notification bubble comes up as well telling me what I am connected to as well.

**Policykit Authentication Agent:**

```
glen@glen-desktop:~$ 
(polkit-gnome-authentication-agent-1:2528): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:2528): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

**glen@glen-desktop:~$
```**

??? Once I run that I have polkit-gnome-authentication-agent-1 in the System Monitor... is it running with errors?

**Print Queue Applet:**

```
glen@glen-desktop:~$ sh -c "sleep 30; exec system-config-printer-applet > /dev/null 2> /dev/null" &
[7] 2529
glen@glen-desktop:~$
```

I have no idea if it's running or not... guess I should plug the printer in... Shouldn't something be running in system monitor though, as a background process?

**Seahorse Daemon:**

```
glen@glen-desktop:~$ seahorse-daemon &
[8] 2535
glen@glen-desktop:~$
```

Adds seahorse daemon to the system monitor.

**Update Notifier:**

```
glen@glen-desktop:~$ update-notifier --startup-delay=120 &
[9] 2548
[8]   Done                    seahorse-daemon
glen@glen-desktop:~$
```

No idea if it's running or not... even after 120 seconds 

BTW: changed to delay=120 from delay=60 as suggested in a different thread. and the [8] is just telling me that seahorse ran successfully (I Think)

**User Folders Update:**

```
glen@glen-desktop:~$ xdg-user-dirs-gtk-update &
[10] 2562
glen@glen-desktop:~$ 
[10]+  Done                    xdg-user-dirs-gtk-update
glen@glen-desktop:~$
```

Apparently did it's job and finished...

**Volume Control Applet:**

```
glen@glen-desktop:~$ gnome-volume-control-applet &
[10] 2565
glen@glen-desktop:~$ 
** (gnome-volume-control-applet:2565): WARNING **: Unable to get default source

glen@glen-desktop:~$
```

gnome-volume-control-applet shows up in system monitor and the icon appears in the notification area. Once I get this to startup properly I'll look into the default source thing, or maybe this is causing it error out and not start initially?

---

### Post by gspat on 2009-12-23
Arghh.. all that checking and going through the system and I WAS in failsafe gnome...

Sigh... live and learn I guess. Thank you for your help!

At least I gave myself a chance to dig down into the system a bit to do some learning!

---

