---
title: "ubuntu server + xfce4 - help"
date: 2010-01-03
forum: General Help
---

### Post by dragilla on 2010-01-03
Hi, I've installed ubuntu server and then added some packages to get a fast / low mem version of xubuntu. This is more less what I did:
```

apt-get install xfce4 xfce4-goodies xfce4-mixer alsa gksu slim firefox-3.5 gnome-icon-theme flashplugin-installer network-manager network-manager-gnome; apt-get purge synaptic

```

Slim is not in the ubutnu repos btw.
Now I have some basic problem which I cannot solve by myself, thus the post.

1. Cannot suspend / hibernate
When I go menu -> log out -> hibernaste or suspend I get the following message:
```

"Suspend and Hibernate are only supported through HAL, which is unavailable"

```
Hald is running and when I type this:
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.GetProperty string:'power_management.can_suspend'

```
"true" is returned

+ when I run: 
```

dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Suspend int32:0

```
The suspend works. However I want it to run the suspension from the menu and from the keyboard shortcut (Fn + F1 on my laptop)

2. Cannot lock screen with ctrl-alt L 
I have xscreensaver installed and running - is the shortcut available only in gnome?

3. No sound
When I try to add the mixer plugin to the xfce4 panel it says;
```

GStreamer was unable to detect any sound devices. Some sound system specific GStreamer packages may be missing. It may also be a permissions problem.

```
Gstreamer0.10-alsa is installed. When I run alsamixer in the console I can set all the levels but still no sound.
Alsa mixer (alsamixer) from the console works as root. Alsa xfce4-mixer works as root. So probably some permissions problem, but what.
Even after setting things as root -> no sound.

4. Network manager
Probably permissions thing again. When I run nm-applet as regular user I get:
```

** (nm-applet:1576): WARNING **: <WARN>  request_name(): Could not acquire the NetworkManagerUserSettings service.
  Error: (9) Connection ":1.27" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file

```
Run by root works fine.

I might add I have start gnome services at startup checked.
Also I run gnome-keyring-daemon manually - it does not start automatically.

If you can help me with any of this please do.

edit: When I run the suspend command as regular user I get the following:
```

Error org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1000 pid=1744 comm="dbus-send) interface="org.freedesktop.Hal.Device.SystemPowerManagement" member="Suspend" error name="(unset)" requested_reply=0 destination="org.freedesktop.Hal" (uid=0 pid=700 comm="hald))

```
So it seems it's another permissions error.

edit2: sound works as root, so it all seems to be a permissions problem (except the locking thing). Any ideas? 

edit3: found a way to lock the screen - it was bound to ather keys in the keyboard settings.
So now I'm left with probably one general permissions problem.


edit4: policykit authentication agent is also started
Come on guys, please help! If I'm asking the wrong questions or I'm doing it in the wrong place please tell me.

regards,
-- 
Luke

---

### Post by dragilla on 2010-01-04
Seems noone here to help me. So I just keep digging.
Found out solution for the nm-applet here: [LINK](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1801527.html)
Also there was this one time when I rebooted and both hibernation and nm-applet worked. Don't know what was different then tho.

Anyway the nm-applet seems to work.
Now the hibernation and gstreamer. Anybody?

update: editing hal.conf fixed the hibernation problem
Still no idea about sound.

To be clear - the sound works as root, and also worked when I installed full xubuntu.
This is what "sudo aplay -L" returns:
```

default:CARD=Intel
    HDA Intel, ALC662 rev1 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 rev1 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

sudo aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
Home directory /home/aga not ours.
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

On the other hand when run as regular user:
```

aga@aga:~$ aplay -l 
aplay: device_list:223: no soundcards found...

```
aplay -L (as regular user) returns nothing

update: adding my user to the audio group fixed the sound :)

---

### Post by Leppie on 2010-01-08
To lock the screen in Xubuntu is CTRL+ALT+DEL, probably the same for XFCE

---

