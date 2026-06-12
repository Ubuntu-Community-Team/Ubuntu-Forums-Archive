---
title: "Ubuntu 10.10 Desktop freezing"
date: 2011-04-29
forum: General Help
---

### Post by jubei52 on 2011-04-29
Hi there,

I have setup a system that I want to use for my htpc with audio/video through HDMI via an nVidia GT210 pci card with a corsair 32 GB nova SSD as the boot drive.

I installed Ubuntu 10.10 desktop version.  I upgraded to the latest nvidia drivers via their website instructions and upgraded alsa to the latest version to get sound working.  I also diabled all my desktop effects and disabled compiz.  I have installed transimssion and added it to the start-up menu of the application list.  I have autologin enabled (there is only one user on this machine).  I also installed samba via "sudo apt-get system-config-samba" andit works  fine - all my shares are visible on my network.

Now my machine is randomly freezing on me and then sending me back to the loginscreen.

I found a hidden file called "xsession-errors.old" and it contains this output, which ahs a number of errors but I am unsure if this is what is causing the problem:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-TENZTq
GNOME_KEYRING_PID=1416
GNOME_KEYRING_CONTROL=/tmp/keyring-TENZTq
GNOME_KEYRING_CONTROL=/tmp/keyring-TENZTq
SSH_AUTH_SOCK=/tmp/keyring-TENZTq/ssh

(polkit-gnome-authentication-agent-1:1496): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1496): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
Initializing nautilus-gdu extension

(nautilus:1500): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
28/04/2011 10:38:57 PM Autoprobing TCP port in (all) network interface
28/04/2011 10:38:57 PM Listening IPv6://[::]:5900
28/04/2011 10:38:57 PM Listening IPv4://0.0.0.0:5900
28/04/2011 10:38:57 PM Autoprobing selected port 5900
28/04/2011 10:38:57 PM Advertising security type: 'TLS' (18)
28/04/2011 10:38:57 PM Advertising authentication type: 'VNC Authentication' (2)
28/04/2011 10:38:57 PM Advertising security type: 'VNC Authentication' (2)
Unable to find a synaptics device.
** Message: Received signal 11, exiting...


(nautilus:1500): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-panel: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
transmission: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
gdu-notification-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gedit: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
<unknown>: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
firefox-bin: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
```

Any help would be GREATLY appreciated - I have been fiddling with this system for weeks now and I haven't been able to get this issue fixed.

---

