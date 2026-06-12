---
title: "Ubuntu crashes randomly to login screen"
date: 2010-11-22
forum: General Help
---

### Post by cheets on 2010-11-22
I upgraded 10.04 to 10.10 (32bit), the upgrade process didn't go that well because first it didn't boot beyond GRUB. Solved this by unplugging my keyboard (my ubuntu is a server machine without keyboard or mouse, I like to use the desktop version through vnc). After that is booted to shell, which was not so nice either. This time it was the legendary nouveau driver which sorry for my language I will never install again (caused major problem twice already). Installed nvidia drivers and got a display for X this time and it booted nicely to login screen. 

My problems have arised since the upgrade, the system will randomly "crash" and go straight to login screen, ending my current session. Sometimes my mouse cursor even changes to the X-mark. I can't see anything in gdm, x11, syslog etc. that would explain the crash. So far I've found best log from .xsession-errors which is here:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=fi_FI.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-DIvnJc
SSH_AUTH_SOCK=/tmp/keyring-DIvnJc/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-DIvnJc
SSH_AUTH_SOCK=/tmp/keyring-DIvnJc/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-DIvnJc
SSH_AUTH_SOCK=/tmp/keyring-DIvnJc/ssh

(polkit-gnome-authentication-agent-1:21781): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:21781): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: applet now removed from the notification area
** (nm-applet:21773): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Initializing nautilus-gdu extension

(nautilus:21774): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
** Message: applet now embedded in the notification area
gnome-session[21683]: WARNING: Could not launch application 'gnome-user-share.desktop': Unable to start application: Lapsiprosessin â€/usr/lib/gnome-user-share/gnome-user-shareâ€ kÃ¤ynnistÃ¤minen epÃ¤onnistui (Tiedostoa tai hakemistoa ei ole)

(exe:22074): Gdk-WARNING **: XID collision, trouble ahead
[21944:22061:290254652476:ERROR:net/base/x509_certificate_nss.cc(658)] CERT_PKIXVerifyCert for celeste failed err=-8172
[21944:22072:290255439991:ERROR:net/base/x509_certificate_nss.cc(658)] CERT_PKIXVerifyCert for celeste failed err=-8172

(exe:22074): Gdk-WARNING **: XID collision, trouble ahead

(exe:22074): Gdk-WARNING **: XID collision, trouble ahead
** (update-notifier:22082): DEBUG: aptdaemon on bus: 0
** (update-notifier:22082): DEBUG: Skipping reboot required

``` 

This log was generated just now as the crash happened again, the whole file was not there before crash because I deleted it after previous crash. 

I get these crashes sometimes 3 in 5 minutes and sometimes 1 in a week. So no rule here. I have chrome, utorrent, sbnc and teamspeak3 running on the server, some other things like apache and x11vnc too, but mostly just those. 

I got a lot IPv6 errors on the same log too, but those were caused by utorrent+too old wine. Didn't remember that upgrade deletes/disables extra-repos and I was running the stable wine (1.2.1) instead of the latest one (1.3.7). Upgrading wine solved the error from utorrent IPv6 connections. 

So any ideas what I could do to fix these crashes? I'm not so much into clean re-install because of all the configuration I'll need to do then. I do have home on a separate partition but there's lots of software to install and configure.

---

### Post by cheets on 2010-11-24
I thought it had something to with corrupted config files so I removed .gnome2, .gnome2_private etc. Then I logged out and there it was, x11vnc crashed and my vnc connection was closed. After investing this I found a thread about x11vnc crashing X soon after logging in [http://wwww.ubuntuforums.org/showthread.php?t=1612704]("http://wwww.ubuntuforums.org/showthread.php?t=1612704") and the problem was luckily solved! So I followed the directions, updated my x11vnc from 0.9.12 to 0.9.13 (don't know if this is necessary) and added the -noxrecord parameter for launching x11vnc. This seemed the help those with the crashing problem and I could also see from my log that there was some errors in recording. 

I'll mark this solved if my issue is now fixed with the -noxrecord parameter.

EDIT: Marked as solved as I don't get the crashes anymore after using the -noxrecord parameter.

---

### Post by skulls on 2011-04-19
Thanks Cheets!

---

