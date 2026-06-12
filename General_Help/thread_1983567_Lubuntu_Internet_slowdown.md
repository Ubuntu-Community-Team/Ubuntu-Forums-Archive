---
title: "Lubuntu Internet slowdown"
date: 2012-05-20
forum: General Help
---

### Post by regor210 on 2012-05-20
It was taking up to 5 minuets to load a web page here at Ubuntu forums.
I tried a tor enabled browser and everything worked fine.

After a few tries and 15 minuets of running Firefox in a terminal I got this

 regor210@regor210-GeForce6100PM-M2:~$ firefox
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-ItITHz/pkcs11: No such file or directory
NOTE: child process received `Goodbye', closing down
regor210@regor210-GeForce6100PM-M2:~$ 

went here /etc/xdg/autostart/ and edited gnome-settings-daemon.desktop and I added the bold text 

[Desktop Entry]
Type=Application
Name=GNOME Settings Daemon
Exec=/usr/lib/gnome-settings-daemon/gnome-settings-daemon
[B]OnlyShowIn=GNOME;LXDE
OnlyShowIn=GNOME;XFCE[/B]
OnlyShowIn=GNOME;Unity
NoDisplay=true
X-GNOME-Autostart-Phase=Initialization
X-GNOME-Autostart-Notify=true
X-GNOME-AutoRestart=true
X-Ubuntu-Gettext-Domain=gnome-settings-daemon

Note. This did not work OnlyShowIn=GNOME;Unity;LXDE;XFCE

These websites were helpful.
[http://laslow.net/2012/05/06/gnome-keyring-issues-in-ubuntu-12-04/](http://laslow.net/2012/05/06/gnome-keyring-issues-in-ubuntu-12-04/)
[https://bugs.launchpad.net/ubuntu/+source/lxde-common/+bug/664206](https://bugs.launchpad.net/ubuntu/+source/lxde-common/+bug/664206)

---

