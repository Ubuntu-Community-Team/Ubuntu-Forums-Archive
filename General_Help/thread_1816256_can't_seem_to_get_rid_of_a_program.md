---
title: "can't seem to get rid of a program"
date: 2011-08-01
forum: General Help
---

### Post by KrisB on 2011-08-01
Hi all,

I'm not sure which topic to even put this under so I'm starting here...

I was on this forum last week getting help with my wireless card, and I got excellent help.  One of the things that I did along the way was uninstall one program (wicd) and reinstall another (network manager).  Afterwards, things worked ok.  Yesterday for some reason I don't understand, the error message I originally got with Wicd installed is back.  I looked in the software center and it says it's not installed.  I looked in synaptic package manager and It doesn't seem to be there.  I tried the command (I learned it the other day- I really know VERY little commands) sudo apt-get --purge remove wicd.  It says it's not installed.  But it still comes up on every boot saying that it's looking for my wireless card and then complains about a d-bus error.  I don't seem to have this program anywhere that I can remove it!!! I've never seen anything like that before!  Can anyone help?  :confused:

I'm using 11.04 and I CAN connect w/ network manager.


Kris

---

### Post by FormatSeize on 2011-08-01
```
sudo apt-get remove --purge NameOfProgram
```

---

### Post by KrisB on 2011-08-01
Only problem is if you re-read the post, I did exactly that and it says it's not installed.  That 0 packages would be removed.  (because they're not there)  That's what is so weird about this!  But thanks for the suggestion!

---

### Post by gandaran on 2011-08-01
> But it still comes up on every boot saying that it's looking for my wireless card and then complains about a d-bus error
whats the exact full error?

---

### Post by KrisB on 2011-08-01
as it finishes booting I get a box that pops up saying:
```
Wicd needs to access your computer's network cards.
``` Then it asks for a password.

When I hit ok or cancel it then gives a new box:
```
Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.
```

When I hit ok it says:
```
The wicd daemon has shut down.  The UI will not function properly until it is restarted.
```

After ok

I can then connect normally.  I previously uninstalled it days ago and the error stopped.  Now it's back even though wicd is not even installed!

---

### Post by gandaran on 2011-08-01
> **KrisB said:**
> as it finishes booting I get a box that pops up saying:
```
Wicd needs to access your computer's network cards.
``` Then it asks for a password.

When I hit ok or cancel it then gives a new box:
```
Could not connect to wicd's D-Bus interface. Check the wicd log for error messages.
```

When I hit ok it says:
```
The wicd daemon has shut down.  The UI will not function properly until it is restarted.
```

After ok

I can then connect normally.  I previously uninstalled it days ago and the error stopped.  Now it's back even though wicd is not even installed!
looks like you still have wicd installed, one sure way of removing programs is to use synaptic package manager and choose always the remove completely option, look again for wicd in synaptic, check that it's fully removed.
> Could not connect to wicd's D-Bus interface. Check the wicd log for error messages
the fix for this error message was to run these commands then reboot the PC, the error should stop showing up.
```
sudo dpkg-reconfigure wicd
sudo update-rc.d wicd defaults
``` 
but if wicd is not installed then it's no use running the commands.

---

### Post by KrisB on 2011-08-01
I did, and I see nothing showing in the "installed" column.

Can't figure out how to put in a screenshot without putting in an outside photosite so I attached one

---

### Post by nipennem on 2011-08-01
Post the output of

```
dpkg -l | grep wicd
```

Also, post the output of:

```
sudo updatedb
sudo locate wicd
```

---

### Post by KrisB on 2011-08-01
[CODEkris@kris:~$ dpkg -l | grep wicd
rc  wicd-daemon                           1.7.0+ds1-6                                wired and wireless network manager - daemon
rc  wicd-kde                              0.2.1-4                                    Wired and wireless network manager - KDE client
kris@kris:~$ 
][/CODE]

```
/home/kris/wicd-1.7.0/encryption/templates/wpa-psk
/home/kris/wicd-1.7.0/gtk/configscript.py
/home/kris/wicd-1.7.0/gtk/gui.py
/home/kris/wicd-1.7.0/gtk/guiutil.py
/home/kris/wicd-1.7.0/gtk/netentry.py
/home/kris/wicd-1.7.0/gtk/prefs.py
/home/kris/wicd-1.7.0/gtk/wicd-client.py
/home/kris/wicd-1.7.0/icons/128px
/home/kris/wicd-1.7.0/icons/16px
/home/kris/wicd-1.7.0/icons/192px
/home/kris/wicd-1.7.0/icons/22px
/home/kris/wicd-1.7.0/icons/24px
/home/kris/wicd-1.7.0/icons/32px
/home/kris/wicd-1.7.0/icons/36px
/home/kris/wicd-1.7.0/icons/48px
/home/kris/wicd-1.7.0/icons/64px
/home/kris/wicd-1.7.0/icons/72px
/home/kris/wicd-1.7.0/icons/96px
/home/kris/wicd-1.7.0/icons/scalable
/home/kris/wicd-1.7.0/icons/128px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/16px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/192px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/22px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/24px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/32px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/36px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/48px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/64px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/72px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/96px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/scalable/wicd-gtk.svg
/home/kris/wicd-1.7.0/images/bad-signal-lock.png
/home/kris/wicd-1.7.0/images/bad-signal.png
/home/kris/wicd-1.7.0/images/both-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/both-bad-signal.png
/home/kris/wicd-1.7.0/images/both-good-signal-lock.png
/home/kris/wicd-1.7.0/images/both-good-signal.png
/home/kris/wicd-1.7.0/images/both-high-signal-lock.png
/home/kris/wicd-1.7.0/images/both-high-signal.png
/home/kris/wicd-1.7.0/images/both-low-signal-lock.png
/home/kris/wicd-1.7.0/images/both-low-signal.png
/home/kris/wicd-1.7.0/images/good-signal-lock.png
/home/kris/wicd-1.7.0/images/good-signal.png
/home/kris/wicd-1.7.0/images/high-signal-lock.png
/home/kris/wicd-1.7.0/images/high-signal.png
/home/kris/wicd-1.7.0/images/idle-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-bad-signal.png
/home/kris/wicd-1.7.0/images/idle-good-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-good-signal.png
/home/kris/wicd-1.7.0/images/idle-high-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-high-signal.png
/home/kris/wicd-1.7.0/images/idle-low-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-low-signal.png
/home/kris/wicd-1.7.0/images/low-signal-lock.png
/home/kris/wicd-1.7.0/images/low-signal.png
/home/kris/wicd-1.7.0/images/no-signal.png
/home/kris/wicd-1.7.0/images/receiving-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-bad-signal.png
/home/kris/wicd-1.7.0/images/receiving-good-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-good-signal.png
/home/kris/wicd-1.7.0/images/receiving-high-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-high-signal.png
/home/kris/wicd-1.7.0/images/receiving-low-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-low-signal.png
/home/kris/wicd-1.7.0/images/signal-100.png
/home/kris/wicd-1.7.0/images/signal-25.png
/home/kris/wicd-1.7.0/images/signal-50.png
/home/kris/wicd-1.7.0/images/signal-75.png
/home/kris/wicd-1.7.0/images/transmitting-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-bad-signal.png
/home/kris/wicd-1.7.0/images/transmitting-good-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-good-signal.png
/home/kris/wicd-1.7.0/images/transmitting-high-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-high-signal.png
/home/kris/wicd-1.7.0/images/transmitting-low-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-low-signal.png
/home/kris/wicd-1.7.0/images/wired-gui.svg
/home/kris/wicd-1.7.0/images/wired.png
/home/kris/wicd-1.7.0/in/init=arch=wicd.in
/home/kris/wicd-1.7.0/in/init=debian=wicd.in
/home/kris/wicd-1.7.0/in/init=default=wicd.in
/home/kris/wicd-1.7.0/in/init=gentoo=wicd.in
/home/kris/wicd-1.7.0/in/init=lunar=wicd.in
/home/kris/wicd-1.7.0/in/init=pld=wicd.in
/home/kris/wicd-1.7.0/in/init=redhat=wicd.in
/home/kris/wicd-1.7.0/in/init=slackware=rc.wicd.in
/home/kris/wicd-1.7.0/in/init=suse=wicd.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-curses.8.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-manager-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-wired-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-wireless-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd.8.in
/home/kris/wicd-1.7.0/in/man=wicd-cli.8.in
/home/kris/wicd-1.7.0/in/man=wicd-curses.8.in
/home/kris/wicd-1.7.0/in/man=wicd-manager-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd-wired-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd-wireless-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd.8.in
/home/kris/wicd-1.7.0/in/other=50-wicd-suspend.sh.in
/home/kris/wicd-1.7.0/in/other=80-wicd-connect.sh.in
/home/kris/wicd-1.7.0/in/other=91wicd.in
/home/kris/wicd-1.7.0/in/other=WHEREAREMYFILES.in
/home/kris/wicd-1.7.0/in/other=wicd.conf.in
/home/kris/wicd-1.7.0/in/scripts=wicd-cli.in
/home/kris/wicd-1.7.0/in/scripts=wicd-client.in
/home/kris/wicd-1.7.0/in/scripts=wicd-curses.in
/home/kris/wicd-1.7.0/in/scripts=wicd-gtk.in
/home/kris/wicd-1.7.0/in/scripts=wicd.in
/home/kris/wicd-1.7.0/in/wicd=wpath.py.in
/home/kris/wicd-1.7.0/in/wpath.py.in
/home/kris/wicd-1.7.0/init/arch
/home/kris/wicd-1.7.0/init/debian
/home/kris/wicd-1.7.0/init/default
/home/kris/wicd-1.7.0/init/gentoo
/home/kris/wicd-1.7.0/init/lunar
/home/kris/wicd-1.7.0/init/pld
/home/kris/wicd-1.7.0/init/redhat
/home/kris/wicd-1.7.0/init/slackware
/home/kris/wicd-1.7.0/init/suse
/home/kris/wicd-1.7.0/init/arch/wicd
/home/kris/wicd-1.7.0/init/debian/wicd
/home/kris/wicd-1.7.0/init/default/wicd
/home/kris/wicd-1.7.0/init/gentoo/wicd
/home/kris/wicd-1.7.0/init/lunar/wicd
/home/kris/wicd-1.7.0/init/pld/wicd
/home/kris/wicd-1.7.0/init/redhat/wicd
/home/kris/wicd-1.7.0/init/slackware/rc.wicd
/home/kris/wicd-1.7.0/init/suse/wicd
/home/kris/wicd-1.7.0/man/nl
/home/kris/wicd-1.7.0/man/wicd-cli.8
/home/kris/wicd-1.7.0/man/wicd-client.1
/home/kris/wicd-1.7.0/man/wicd-curses.8
/home/kris/wicd-1.7.0/man/wicd-manager-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd-wired-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd-wireless-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd.8
/home/kris/wicd-1.7.0/man/nl/wicd-client.1
/home/kris/wicd-1.7.0/man/nl/wicd-curses.8
/home/kris/wicd-1.7.0/man/nl/wicd-manager-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd-wired-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd-wireless-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd.8
/home/kris/wicd-1.7.0/other/.empty_on_purpose
/home/kris/wicd-1.7.0/other/50-wicd-suspend.sh
/home/kris/wicd-1.7.0/other/80-wicd-connect.sh
/home/kris/wicd-1.7.0/other/91wicd
/home/kris/wicd-1.7.0/other/WHEREAREMYFILES
/home/kris/wicd-1.7.0/other/dhclient.conf.template.default
/home/kris/wicd-1.7.0/other/wicd-gtk.xpm
/home/kris/wicd-1.7.0/other/wicd-tray.desktop
/home/kris/wicd-1.7.0/other/wicd.conf
/home/kris/wicd-1.7.0/other/wicd.desktop
/home/kris/wicd-1.7.0/scripts/wicd
/home/kris/wicd-1.7.0/scripts/wicd-cli
/home/kris/wicd-1.7.0/scripts/wicd-client
/home/kris/wicd-1.7.0/scripts/wicd-curses
/home/kris/wicd-1.7.0/scripts/wicd-gtk
/home/kris/wicd-1.7.0/tests/__init__.py
/home/kris/wicd-1.7.0/tests/testmisc.py
/home/kris/wicd-1.7.0/tests/testwnettools.py
/home/kris/wicd-1.7.0/translations/ar_EG
/home/kris/wicd-1.7.0/translations/ar_PS
/home/kris/wicd-1.7.0/translations/bg
/home/kris/wicd-1.7.0/translations/ca
/home/kris/wicd-1.7.0/translations/cs
/home/kris/wicd-1.7.0/translations/da
/home/kris/wicd-1.7.0/translations/de
/home/kris/wicd-1.7.0/translations/de_DE
/home/kris/wicd-1.7.0/translations/el
/home/kris/wicd-1.7.0/translations/en_CA
/home/kris/wicd-1.7.0/translations/eo
/home/kris/wicd-1.7.0/translations/es
/home/kris/wicd-1.7.0/translations/es_AR
/home/kris/wicd-1.7.0/translations/es_CL
/home/kris/wicd-1.7.0/translations/es_ES
/home/kris/wicd-1.7.0/translations/es_GT
/home/kris/wicd-1.7.0/translations/es_MX
/home/kris/wicd-1.7.0/translations/es_NI
/home/kris/wicd-1.7.0/translations/es_VE
/home/kris/wicd-1.7.0/translations/et
/home/kris/wicd-1.7.0/translations/eu
/home/kris/wicd-1.7.0/translations/fa
/home/kris/wicd-1.7.0/translations/fi
/home/kris/wicd-1.7.0/translations/fr
/home/kris/wicd-1.7.0/translations/fr_CA
/home/kris/wicd-1.7.0/translations/fr_FR
/home/kris/wicd-1.7.0/translations/gl
/home/kris/wicd-1.7.0/translations/he
/home/kris/wicd-1.7.0/translations/hr_HR
/home/kris/wicd-1.7.0/translations/hu
/home/kris/wicd-1.7.0/translations/id
/home/kris/wicd-1.7.0/translations/it
/home/kris/wicd-1.7.0/translations/it_IT
/home/kris/wicd-1.7.0/translations/ja
/home/kris/wicd-1.7.0/translations/ka
/home/kris/wicd-1.7.0/translations/kk
/home/kris/wicd-1.7.0/translations/ko
/home/kris/wicd-1.7.0/translations/lt
/home/kris/wicd-1.7.0/translations/lv
/home/kris/wicd-1.7.0/translations/ml
/home/kris/wicd-1.7.0/translations/nl
/home/kris/wicd-1.7.0/translations/nl_NL
/home/kris/wicd-1.7.0/translations/no
/home/kris/wicd-1.7.0/translations/pl
/home/kris/wicd-1.7.0/translations/pt
/home/kris/wicd-1.7.0/translations/pt_BR
/home/kris/wicd-1.7.0/translations/ro
/home/kris/wicd-1.7.0/translations/ru
/home/kris/wicd-1.7.0/translations/ru_RU
/home/kris/wicd-1.7.0/translations/sk
/home/kris/wicd-1.7.0/translations/sl
/home/kris/wicd-1.7.0/translations/sr
/home/kris/wicd-1.7.0/translations/sv
/home/kris/wicd-1.7.0/translations/te
/home/kris/wicd-1.7.0/translations/tr
/home/kris/wicd-1.7.0/translations/uk
/home/kris/wicd-1.7.0/translations/vi
/home/kris/wicd-1.7.0/translations/zh_CN
/home/kris/wicd-1.7.0/translations/zh_HK
/home/kris/wicd-1.7.0/translations/zh_TW
/home/kris/wicd-1.7.0/translations/ar_EG/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ar_EG/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ar_PS/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ar_PS/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/bg/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/bg/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ca/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ca/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/cs/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/cs/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/da/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/da/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/de/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/de/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/de_DE/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/de_DE/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/el/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/el/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/en_CA/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/en_CA/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/eo/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/eo/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_AR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_AR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_CL/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_CL/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_ES/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_ES/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_GT/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_GT/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_MX/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_MX/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_NI/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_NI/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_VE/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_VE/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/et/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/et/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/eu/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/eu/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fa/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fa/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fi/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fi/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr_CA/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr_CA/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr_FR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr_FR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/gl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/gl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/he/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/he/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/hr_HR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/hr_HR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/hu/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/hu/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/id/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/id/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/it/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/it/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/it_IT/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/it_IT/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ja/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ja/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ka/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ka/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/kk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/kk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ko/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ko/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/lt/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/lt/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/lv/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/lv/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ml/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ml/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/nl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/nl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/nl_NL/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/nl_NL/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/no/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/no/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pt/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pt/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pt_BR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pt_BR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ro/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ro/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ru/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ru/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ru_RU/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ru_RU/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sv/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sv/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/te/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/te/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/tr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/tr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/uk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/uk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/vi/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/vi/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_CN/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_CN/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_HK/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_HK/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_TW/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_TW/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/wicd/__init__.py
/home/kris/wicd-1.7.0/wicd/autoconnect.py
/home/kris/wicd-1.7.0/wicd/backend.py
/home/kris/wicd-1.7.0/wicd/backends
/home/kris/wicd-1.7.0/wicd/configmanager.py
/home/kris/wicd-1.7.0/wicd/dbusmanager.py
/home/kris/wicd-1.7.0/wicd/logfile.py
/home/kris/wicd-1.7.0/wicd/misc.py
/home/kris/wicd-1.7.0/wicd/monitor.py
/home/kris/wicd-1.7.0/wicd/networking.py
/home/kris/wicd-1.7.0/wicd/suspend.py
/home/kris/wicd-1.7.0/wicd/translations.py
/home/kris/wicd-1.7.0/wicd/wicd-daemon.py
/home/kris/wicd-1.7.0/wicd/wnettools.py
/home/kris/wicd-1.7.0/wicd/wpath.py
/home/kris/wicd-1.7.0/wicd/backends/__init__.py
/home/kris/wicd-1.7.0/wicd/backends/be-external.py
/home/kris/wicd-1.7.0/wicd/backends/be-ioctl.py
/usr/bin/wicd-cli
/usr/bin/wicd-client
/usr/bin/wicd-curses
/usr/bin/wicd-gtk
/usr/local/lib/python2.7/dist-packages/wicd
/usr/local/lib/python2.7/dist-packages/wicd/__init__.py
/usr/local/lib/python2.7/dist-packages/wicd/__init__.pyc
/usr/local/lib/python2.7/dist-packages/wicd/__init__.pyo
/usr/local/lib/python2.7/dist-packages/wicd/backend.py
/usr/local/lib/python2.7/dist-packages/wicd/backend.pyc
/usr/local/lib/python2.7/dist-packages/wicd/backend.pyo
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.py
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.pyc
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.pyo
/usr/local/lib/python2.7/dist-packages/wicd/dbusmanager.py
/usr/local/lib/python2.7/dist-packages/wicd/dbusmanager.pyc
/usr/local/lib/python2.7/dist-packages/wicd/logfile.py
/usr/local/lib/python2.7/dist-packages/wicd/logfile.pyc
/usr/local/lib/python2.7/dist-packages/wicd/logfile.pyo
/usr/local/lib/python2.7/dist-packages/wicd/misc.py
/usr/local/lib/python2.7/dist-packages/wicd/misc.pyc
/usr/local/lib/python2.7/dist-packages/wicd/misc.pyo
/usr/local/lib/python2.7/dist-packages/wicd/networking.py
/usr/local/lib/python2.7/dist-packages/wicd/networking.pyc
/usr/local/lib/python2.7/dist-packages/wicd/networking.pyo
/usr/local/lib/python2.7/dist-packages/wicd/translations.py
/usr/local/lib/python2.7/dist-packages/wicd/translations.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.py
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.pyo
/usr/local/lib/python2.7/dist-packages/wicd/wpath.py
/usr/local/lib/python2.7/dist-packages/wicd/wpath.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wpath.pyo
/usr/share/wicd
/usr/share/app-install/desktop/kde4___wicd-kde.desktop
/usr/share/app-install/desktop/wicd.desktop
/usr/share/app-install/icons/wicd-gtk.png
/usr/share/applications/wicd.desktop
/usr/share/autostart/wicd-tray.desktop
/usr/share/doc/wicd
/usr/share/doc/wicd/AUTHORS
/usr/share/doc/wicd/CHANGES
/usr/share/doc/wicd/INSTALL
/usr/share/doc/wicd/LICENSE
/usr/share/doc/wicd/README
/usr/share/doc/wicd/README.cli
/usr/share/doc/wicd/README.curses
/usr/share/icons/hicolor/128x128/apps/wicd-gtk.png
/usr/share/icons/hicolor/16x16/apps/wicd-gtk.png
/usr/share/icons/hicolor/192x192/apps/wicd-gtk.png
/usr/share/icons/hicolor/22x22/apps/wicd-gtk.png
/usr/share/icons/hicolor/24x24/apps/wicd-gtk.png
/usr/share/icons/hicolor/32x32/apps/wicd-gtk.png
/usr/share/icons/hicolor/36x36/apps/wicd-gtk.png
/usr/share/icons/hicolor/48x48/apps/wicd-gtk.png
/usr/share/icons/hicolor/64x64/apps/wicd-gtk.png
/usr/share/icons/hicolor/72x72/apps/wicd-gtk.png
/usr/share/icons/hicolor/96x96/apps/wicd-gtk.png
/usr/share/icons/hicolor/scalable/apps/wicd-gtk.svg
/usr/share/man/man1/wicd-client.1
/usr/share/man/man5/wicd-manager-settings.conf.5
/usr/share/man/man5/wicd-wired-settings.conf.5
/usr/share/man/man5/wicd-wireless-settings.conf.5
/usr/share/man/man8/wicd-cli.8
/usr/share/man/man8/wicd-curses.8
/usr/share/man/man8/wicd.8
/usr/share/man/nl/man1/wicd-client.1
/usr/share/man/nl/man5/wicd-manager-settings.conf.5
/usr/share/man/nl/man5/wicd-wired-settings.conf.5
/usr/share/man/nl/man5/wicd-wireless-settings.conf.5
/usr/share/man/nl/man8/wicd-curses.8
/usr/share/man/nl/man8/wicd.8
/usr/share/pixmaps/wicd
/usr/share/pixmaps/wicd-gtk.xpm
/usr/share/pixmaps/wicd/bad-signal-lock.png
/usr/share/pixmaps/wicd/bad-signal.png
/usr/share/pixmaps/wicd/both-bad-signal-lock.png
/usr/share/pixmaps/wicd/both-bad-signal.png
/usr/share/pixmaps/wicd/both-good-signal-lock.png
/usr/share/pixmaps/wicd/both-good-signal.png
/usr/share/pixmaps/wicd/both-high-signal-lock.png
/usr/share/pixmaps/wicd/both-high-signal.png
/usr/share/pixmaps/wicd/both-low-signal-lock.png
/usr/share/pixmaps/wicd/both-low-signal.png
/usr/share/pixmaps/wicd/good-signal-lock.png
/usr/share/pixmaps/wicd/good-signal.png
/usr/share/pixmaps/wicd/high-signal-lock.png
/usr/share/pixmaps/wicd/high-signal.png
/usr/share/pixmaps/wicd/idle-bad-signal-lock.png
/usr/share/pixmaps/wicd/idle-bad-signal.png
/usr/share/pixmaps/wicd/idle-good-signal-lock.png
/usr/share/pixmaps/wicd/idle-good-signal.png
/usr/share/pixmaps/wicd/idle-high-signal-lock.png
/usr/share/pixmaps/wicd/idle-high-signal.png
/usr/share/pixmaps/wicd/idle-low-signal-lock.png
/usr/share/pixmaps/wicd/idle-low-signal.png
/usr/share/pixmaps/wicd/low-signal-lock.png
/usr/share/pixmaps/wicd/low-signal.png
/usr/share/pixmaps/wicd/no-signal.png
/usr/share/pixmaps/wicd/receiving-bad-signal-lock.png
/usr/share/pixmaps/wicd/receiving-bad-signal.png
/usr/share/pixmaps/wicd/receiving-good-signal-lock.png
/usr/share/pixmaps/wicd/receiving-good-signal.png
/usr/share/pixmaps/wicd/receiving-high-signal-lock.png
/usr/share/pixmaps/wicd/receiving-high-signal.png
/usr/share/pixmaps/wicd/receiving-low-signal-lock.png
/usr/share/pixmaps/wicd/receiving-low-signal.png
/usr/share/pixmaps/wicd/signal-100.png
/usr/share/pixmaps/wicd/signal-25.png
/usr/share/pixmaps/wicd/signal-50.png
/usr/share/pixmaps/wicd/signal-75.png
/usr/share/pixmaps/wicd/transmitting-bad-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-bad-signal.png
/usr/share/pixmaps/wicd/transmitting-good-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-good-signal.png
/usr/share/pixmaps/wicd/transmitting-high-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-high-signal.png
/usr/share/pixmaps/wicd/transmitting-low-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-low-signal.png
/usr/share/pixmaps/wicd/wired-gui.svg
/usr/share/pixmaps/wicd/wired.png
/usr/share/wicd/backends
/usr/share/wicd/cli
/usr/share/wicd/curses
/usr/share/wicd/gtk
/usr/share/wicd/cli/wicd-cli.py
/usr/share/wicd/curses/configscript_curses.py
/usr/share/wicd/curses/curses_misc.py
/usr/share/wicd/curses/netentry_curses.py
/usr/share/wicd/curses/prefs_curses.py
/usr/share/wicd/curses/wicd-curses.py
/usr/share/wicd/gtk/configscript.py
/usr/share/wicd/gtk/gui.py
/usr/share/wicd/gtk/guiutil.py
/usr/share/wicd/gtk/netentry.py
/usr/share/wicd/gtk/prefs.py
/usr/share/wicd/gtk/wicd-client.py
/usr/share/wicd/gtk/wicd.glade
/var/cache/apt/archives/python-wicd_1.7.0+ds1-6_all.deb
/var/cache/apt/archives/wicd-daemon_1.7.0+ds1-6_all.deb
/var/cache/apt/archives/wicd-kde_0.2.1-4_i386.deb
/var/lib/wicd
/var/lib/dpkg/info/wicd-daemon.list
/var/lib/dpkg/info/wicd-daemon.postrm
/var/lib/dpkg/info/wicd-kde.list
/var/lib/update-rc.d/wicd
/var/lib/wicd/WHEREAREMYFILES
/var/lib/wicd/configurations
/var/lib/wicd/resolv.conf.orig
/var/lib/wicd/configurations/.empty_on_purpose
/var/log/wicd
/var/log/wicd/.empty_on_purpose
/var/log/wicd/wicd.log

```

It seems to have cut off the top b/c there was so much!!  I'm thoroughly confused!  I purged it and it said it wasn't installed!

---

### Post by nipennem on 2011-08-01
> **KrisB said:**
> [CODEkris@kris:~$ dpkg -l | grep wicd
rc  wicd-daemon                           1.7.0+ds1-6                                wired and wireless network manager - daemon
rc  wicd-kde                              0.2.1-4                                    Wired and wireless network manager - KDE client
kris@kris:~$ 
][/CODE]



Try 

```

sudo dpkg --purge wicd-daemon wicd-kde

```Because a status of 'rc' indicates you have remaining configuration files... which means wicd was not purged. What you need to purge is wicd-daemon and wicd-kde. There seems to be no wicd package (at least not on your system)!!

[COLOR=Red]**EDIT:**[/COLOR]

When you're done, repost output of

```

sudo updatedb
sudo locate wicd

```

---

### Post by KrisB on 2011-08-01
ok I did, thanks! Should I restart and see if that fixed it?

[CODE][/home/kris/wicd-1.7.0/encryption/templates
/home/kris/wicd-1.7.0/encryption/templates/active
/home/kris/wicd-1.7.0/encryption/templates/eap
/home/kris/wicd-1.7.0/encryption/templates/eap-tls
/home/kris/wicd-1.7.0/encryption/templates/leap
/home/kris/wicd-1.7.0/encryption/templates/peap
/home/kris/wicd-1.7.0/encryption/templates/peap-tkip
/home/kris/wicd-1.7.0/encryption/templates/ttls
/home/kris/wicd-1.7.0/encryption/templates/wep-hex
/home/kris/wicd-1.7.0/encryption/templates/wep-passphrase
/home/kris/wicd-1.7.0/encryption/templates/wep-shared
/home/kris/wicd-1.7.0/encryption/templates/wpa
/home/kris/wicd-1.7.0/encryption/templates/wpa-psk
/home/kris/wicd-1.7.0/gtk/configscript.py
/home/kris/wicd-1.7.0/gtk/gui.py
/home/kris/wicd-1.7.0/gtk/guiutil.py
/home/kris/wicd-1.7.0/gtk/netentry.py
/home/kris/wicd-1.7.0/gtk/prefs.py
/home/kris/wicd-1.7.0/gtk/wicd-client.py
/home/kris/wicd-1.7.0/icons/128px
/home/kris/wicd-1.7.0/icons/16px
/home/kris/wicd-1.7.0/icons/192px
/home/kris/wicd-1.7.0/icons/22px
/home/kris/wicd-1.7.0/icons/24px
/home/kris/wicd-1.7.0/icons/32px
/home/kris/wicd-1.7.0/icons/36px
/home/kris/wicd-1.7.0/icons/48px
/home/kris/wicd-1.7.0/icons/64px
/home/kris/wicd-1.7.0/icons/72px
/home/kris/wicd-1.7.0/icons/96px
/home/kris/wicd-1.7.0/icons/scalable
/home/kris/wicd-1.7.0/icons/128px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/16px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/192px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/22px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/24px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/32px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/36px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/48px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/64px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/72px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/96px/wicd-gtk.png
/home/kris/wicd-1.7.0/icons/scalable/wicd-gtk.svg
/home/kris/wicd-1.7.0/images/bad-signal-lock.png
/home/kris/wicd-1.7.0/images/bad-signal.png
/home/kris/wicd-1.7.0/images/both-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/both-bad-signal.png
/home/kris/wicd-1.7.0/images/both-good-signal-lock.png
/home/kris/wicd-1.7.0/images/both-good-signal.png
/home/kris/wicd-1.7.0/images/both-high-signal-lock.png
/home/kris/wicd-1.7.0/images/both-high-signal.png
/home/kris/wicd-1.7.0/images/both-low-signal-lock.png
/home/kris/wicd-1.7.0/images/both-low-signal.png
/home/kris/wicd-1.7.0/images/good-signal-lock.png
/home/kris/wicd-1.7.0/images/good-signal.png
/home/kris/wicd-1.7.0/images/high-signal-lock.png
/home/kris/wicd-1.7.0/images/high-signal.png
/home/kris/wicd-1.7.0/images/idle-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-bad-signal.png
/home/kris/wicd-1.7.0/images/idle-good-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-good-signal.png
/home/kris/wicd-1.7.0/images/idle-high-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-high-signal.png
/home/kris/wicd-1.7.0/images/idle-low-signal-lock.png
/home/kris/wicd-1.7.0/images/idle-low-signal.png
/home/kris/wicd-1.7.0/images/low-signal-lock.png
/home/kris/wicd-1.7.0/images/low-signal.png
/home/kris/wicd-1.7.0/images/no-signal.png
/home/kris/wicd-1.7.0/images/receiving-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-bad-signal.png
/home/kris/wicd-1.7.0/images/receiving-good-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-good-signal.png
/home/kris/wicd-1.7.0/images/receiving-high-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-high-signal.png
/home/kris/wicd-1.7.0/images/receiving-low-signal-lock.png
/home/kris/wicd-1.7.0/images/receiving-low-signal.png
/home/kris/wicd-1.7.0/images/signal-100.png
/home/kris/wicd-1.7.0/images/signal-25.png
/home/kris/wicd-1.7.0/images/signal-50.png
/home/kris/wicd-1.7.0/images/signal-75.png
/home/kris/wicd-1.7.0/images/transmitting-bad-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-bad-signal.png
/home/kris/wicd-1.7.0/images/transmitting-good-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-good-signal.png
/home/kris/wicd-1.7.0/images/transmitting-high-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-high-signal.png
/home/kris/wicd-1.7.0/images/transmitting-low-signal-lock.png
/home/kris/wicd-1.7.0/images/transmitting-low-signal.png
/home/kris/wicd-1.7.0/images/wired-gui.svg
/home/kris/wicd-1.7.0/images/wired.png
/home/kris/wicd-1.7.0/in/init=arch=wicd.in
/home/kris/wicd-1.7.0/in/init=debian=wicd.in
/home/kris/wicd-1.7.0/in/init=default=wicd.in
/home/kris/wicd-1.7.0/in/init=gentoo=wicd.in
/home/kris/wicd-1.7.0/in/init=lunar=wicd.in
/home/kris/wicd-1.7.0/in/init=pld=wicd.in
/home/kris/wicd-1.7.0/in/init=redhat=wicd.in
/home/kris/wicd-1.7.0/in/init=slackware=rc.wicd.in
/home/kris/wicd-1.7.0/in/init=suse=wicd.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-curses.8.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-manager-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-wired-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd-wireless-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=nl=wicd.8.in
/home/kris/wicd-1.7.0/in/man=wicd-cli.8.in
/home/kris/wicd-1.7.0/in/man=wicd-curses.8.in
/home/kris/wicd-1.7.0/in/man=wicd-manager-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd-wired-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd-wireless-settings.conf.5.in
/home/kris/wicd-1.7.0/in/man=wicd.8.in
/home/kris/wicd-1.7.0/in/other=50-wicd-suspend.sh.in
/home/kris/wicd-1.7.0/in/other=80-wicd-connect.sh.in
/home/kris/wicd-1.7.0/in/other=91wicd.in
/home/kris/wicd-1.7.0/in/other=WHEREAREMYFILES.in
/home/kris/wicd-1.7.0/in/other=wicd.conf.in
/home/kris/wicd-1.7.0/in/scripts=wicd-cli.in
/home/kris/wicd-1.7.0/in/scripts=wicd-client.in
/home/kris/wicd-1.7.0/in/scripts=wicd-curses.in
/home/kris/wicd-1.7.0/in/scripts=wicd-gtk.in
/home/kris/wicd-1.7.0/in/scripts=wicd.in
/home/kris/wicd-1.7.0/in/wicd=wpath.py.in
/home/kris/wicd-1.7.0/in/wpath.py.in
/home/kris/wicd-1.7.0/init/arch
/home/kris/wicd-1.7.0/init/debian
/home/kris/wicd-1.7.0/init/default
/home/kris/wicd-1.7.0/init/gentoo
/home/kris/wicd-1.7.0/init/lunar
/home/kris/wicd-1.7.0/init/pld
/home/kris/wicd-1.7.0/init/redhat
/home/kris/wicd-1.7.0/init/slackware
/home/kris/wicd-1.7.0/init/suse
/home/kris/wicd-1.7.0/init/arch/wicd
/home/kris/wicd-1.7.0/init/debian/wicd
/home/kris/wicd-1.7.0/init/default/wicd
/home/kris/wicd-1.7.0/init/gentoo/wicd
/home/kris/wicd-1.7.0/init/lunar/wicd
/home/kris/wicd-1.7.0/init/pld/wicd
/home/kris/wicd-1.7.0/init/redhat/wicd
/home/kris/wicd-1.7.0/init/slackware/rc.wicd
/home/kris/wicd-1.7.0/init/suse/wicd
/home/kris/wicd-1.7.0/man/nl
/home/kris/wicd-1.7.0/man/wicd-cli.8
/home/kris/wicd-1.7.0/man/wicd-client.1
/home/kris/wicd-1.7.0/man/wicd-curses.8
/home/kris/wicd-1.7.0/man/wicd-manager-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd-wired-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd-wireless-settings.conf.5
/home/kris/wicd-1.7.0/man/wicd.8
/home/kris/wicd-1.7.0/man/nl/wicd-client.1
/home/kris/wicd-1.7.0/man/nl/wicd-curses.8
/home/kris/wicd-1.7.0/man/nl/wicd-manager-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd-wired-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd-wireless-settings.conf.5
/home/kris/wicd-1.7.0/man/nl/wicd.8
/home/kris/wicd-1.7.0/other/.empty_on_purpose
/home/kris/wicd-1.7.0/other/50-wicd-suspend.sh
/home/kris/wicd-1.7.0/other/80-wicd-connect.sh
/home/kris/wicd-1.7.0/other/91wicd
/home/kris/wicd-1.7.0/other/WHEREAREMYFILES
/home/kris/wicd-1.7.0/other/dhclient.conf.template.default
/home/kris/wicd-1.7.0/other/wicd-gtk.xpm
/home/kris/wicd-1.7.0/other/wicd-tray.desktop
/home/kris/wicd-1.7.0/other/wicd.conf
/home/kris/wicd-1.7.0/other/wicd.desktop
/home/kris/wicd-1.7.0/scripts/wicd
/home/kris/wicd-1.7.0/scripts/wicd-cli
/home/kris/wicd-1.7.0/scripts/wicd-client
/home/kris/wicd-1.7.0/scripts/wicd-curses
/home/kris/wicd-1.7.0/scripts/wicd-gtk
/home/kris/wicd-1.7.0/tests/__init__.py
/home/kris/wicd-1.7.0/tests/testmisc.py
/home/kris/wicd-1.7.0/tests/testwnettools.py
/home/kris/wicd-1.7.0/translations/ar_EG
/home/kris/wicd-1.7.0/translations/ar_PS
/home/kris/wicd-1.7.0/translations/bg
/home/kris/wicd-1.7.0/translations/ca
/home/kris/wicd-1.7.0/translations/cs
/home/kris/wicd-1.7.0/translations/da
/home/kris/wicd-1.7.0/translations/de
/home/kris/wicd-1.7.0/translations/de_DE
/home/kris/wicd-1.7.0/translations/el
/home/kris/wicd-1.7.0/translations/en_CA
/home/kris/wicd-1.7.0/translations/eo
/home/kris/wicd-1.7.0/translations/es
/home/kris/wicd-1.7.0/translations/es_AR
/home/kris/wicd-1.7.0/translations/es_CL
/home/kris/wicd-1.7.0/translations/es_ES
/home/kris/wicd-1.7.0/translations/es_GT
/home/kris/wicd-1.7.0/translations/es_MX
/home/kris/wicd-1.7.0/translations/es_NI
/home/kris/wicd-1.7.0/translations/es_VE
/home/kris/wicd-1.7.0/translations/et
/home/kris/wicd-1.7.0/translations/eu
/home/kris/wicd-1.7.0/translations/fa
/home/kris/wicd-1.7.0/translations/fi
/home/kris/wicd-1.7.0/translations/fr
/home/kris/wicd-1.7.0/translations/fr_CA
/home/kris/wicd-1.7.0/translations/fr_FR
/home/kris/wicd-1.7.0/translations/gl
/home/kris/wicd-1.7.0/translations/he
/home/kris/wicd-1.7.0/translations/hr_HR
/home/kris/wicd-1.7.0/translations/hu
/home/kris/wicd-1.7.0/translations/id
/home/kris/wicd-1.7.0/translations/it
/home/kris/wicd-1.7.0/translations/it_IT
/home/kris/wicd-1.7.0/translations/ja
/home/kris/wicd-1.7.0/translations/ka
/home/kris/wicd-1.7.0/translations/kk
/home/kris/wicd-1.7.0/translations/ko
/home/kris/wicd-1.7.0/translations/lt
/home/kris/wicd-1.7.0/translations/lv
/home/kris/wicd-1.7.0/translations/ml
/home/kris/wicd-1.7.0/translations/nl
/home/kris/wicd-1.7.0/translations/nl_NL
/home/kris/wicd-1.7.0/translations/no
/home/kris/wicd-1.7.0/translations/pl
/home/kris/wicd-1.7.0/translations/pt
/home/kris/wicd-1.7.0/translations/pt_BR
/home/kris/wicd-1.7.0/translations/ro
/home/kris/wicd-1.7.0/translations/ru
/home/kris/wicd-1.7.0/translations/ru_RU
/home/kris/wicd-1.7.0/translations/sk
/home/kris/wicd-1.7.0/translations/sl
/home/kris/wicd-1.7.0/translations/sr
/home/kris/wicd-1.7.0/translations/sv
/home/kris/wicd-1.7.0/translations/te
/home/kris/wicd-1.7.0/translations/tr
/home/kris/wicd-1.7.0/translations/uk
/home/kris/wicd-1.7.0/translations/vi
/home/kris/wicd-1.7.0/translations/zh_CN
/home/kris/wicd-1.7.0/translations/zh_HK
/home/kris/wicd-1.7.0/translations/zh_TW
/home/kris/wicd-1.7.0/translations/ar_EG/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ar_EG/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ar_PS/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ar_PS/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/bg/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/bg/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ca/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ca/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/cs/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/cs/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/da/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/da/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/de/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/de/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/de_DE/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/de_DE/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/el/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/el/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/en_CA/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/en_CA/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/eo/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/eo/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_AR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_AR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_CL/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_CL/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_ES/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_ES/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_GT/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_GT/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_MX/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_MX/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_NI/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_NI/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/es_VE/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/es_VE/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/et/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/et/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/eu/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/eu/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fa/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fa/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fi/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fi/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr_CA/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr_CA/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/fr_FR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/fr_FR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/gl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/gl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/he/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/he/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/hr_HR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/hr_HR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/hu/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/hu/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/id/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/id/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/it/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/it/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/it_IT/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/it_IT/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ja/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ja/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ka/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ka/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/kk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/kk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ko/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ko/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/lt/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/lt/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/lv/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/lv/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ml/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ml/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/nl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/nl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/nl_NL/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/nl_NL/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/no/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/no/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pt/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pt/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/pt_BR/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/pt_BR/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ro/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ro/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ru/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ru/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/ru_RU/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/ru_RU/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sl/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sl/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/sv/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/sv/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/te/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/te/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/tr/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/tr/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/uk/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/uk/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/vi/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/vi/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_CN/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_CN/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_HK/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_HK/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/translations/zh_TW/LC_MESSAGES
/home/kris/wicd-1.7.0/translations/zh_TW/LC_MESSAGES/wicd.mo
/home/kris/wicd-1.7.0/wicd/__init__.py
/home/kris/wicd-1.7.0/wicd/autoconnect.py
/home/kris/wicd-1.7.0/wicd/backend.py
/home/kris/wicd-1.7.0/wicd/backends
/home/kris/wicd-1.7.0/wicd/configmanager.py
/home/kris/wicd-1.7.0/wicd/dbusmanager.py
/home/kris/wicd-1.7.0/wicd/logfile.py
/home/kris/wicd-1.7.0/wicd/misc.py
/home/kris/wicd-1.7.0/wicd/monitor.py
/home/kris/wicd-1.7.0/wicd/networking.py
/home/kris/wicd-1.7.0/wicd/suspend.py
/home/kris/wicd-1.7.0/wicd/translations.py
/home/kris/wicd-1.7.0/wicd/wicd-daemon.py
/home/kris/wicd-1.7.0/wicd/wnettools.py
/home/kris/wicd-1.7.0/wicd/wpath.py
/home/kris/wicd-1.7.0/wicd/backends/__init__.py
/home/kris/wicd-1.7.0/wicd/backends/be-external.py
/home/kris/wicd-1.7.0/wicd/backends/be-ioctl.py
/usr/bin/wicd-cli
/usr/bin/wicd-client
/usr/bin/wicd-curses
/usr/bin/wicd-gtk
/usr/local/lib/python2.7/dist-packages/wicd
/usr/local/lib/python2.7/dist-packages/wicd/__init__.py
/usr/local/lib/python2.7/dist-packages/wicd/__init__.pyc
/usr/local/lib/python2.7/dist-packages/wicd/__init__.pyo
/usr/local/lib/python2.7/dist-packages/wicd/backend.py
/usr/local/lib/python2.7/dist-packages/wicd/backend.pyc
/usr/local/lib/python2.7/dist-packages/wicd/backend.pyo
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.py
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.pyc
/usr/local/lib/python2.7/dist-packages/wicd/configmanager.pyo
/usr/local/lib/python2.7/dist-packages/wicd/dbusmanager.py
/usr/local/lib/python2.7/dist-packages/wicd/dbusmanager.pyc
/usr/local/lib/python2.7/dist-packages/wicd/logfile.py
/usr/local/lib/python2.7/dist-packages/wicd/logfile.pyc
/usr/local/lib/python2.7/dist-packages/wicd/logfile.pyo
/usr/local/lib/python2.7/dist-packages/wicd/misc.py
/usr/local/lib/python2.7/dist-packages/wicd/misc.pyc
/usr/local/lib/python2.7/dist-packages/wicd/misc.pyo
/usr/local/lib/python2.7/dist-packages/wicd/networking.py
/usr/local/lib/python2.7/dist-packages/wicd/networking.pyc
/usr/local/lib/python2.7/dist-packages/wicd/networking.pyo
/usr/local/lib/python2.7/dist-packages/wicd/translations.py
/usr/local/lib/python2.7/dist-packages/wicd/translations.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.py
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wnettools.pyo
/usr/local/lib/python2.7/dist-packages/wicd/wpath.py
/usr/local/lib/python2.7/dist-packages/wicd/wpath.pyc
/usr/local/lib/python2.7/dist-packages/wicd/wpath.pyo
/usr/share/wicd
/usr/share/app-install/desktop/kde4___wicd-kde.desktop
/usr/share/app-install/desktop/wicd.desktop
/usr/share/app-install/icons/wicd-gtk.png
/usr/share/applications/wicd.desktop
/usr/share/autostart/wicd-tray.desktop
/usr/share/doc/wicd
/usr/share/doc/wicd/AUTHORS
/usr/share/doc/wicd/CHANGES
/usr/share/doc/wicd/INSTALL
/usr/share/doc/wicd/LICENSE
/usr/share/doc/wicd/README
/usr/share/doc/wicd/README.cli
/usr/share/doc/wicd/README.curses
/usr/share/icons/hicolor/128x128/apps/wicd-gtk.png
/usr/share/icons/hicolor/16x16/apps/wicd-gtk.png
/usr/share/icons/hicolor/192x192/apps/wicd-gtk.png
/usr/share/icons/hicolor/22x22/apps/wicd-gtk.png
/usr/share/icons/hicolor/24x24/apps/wicd-gtk.png
/usr/share/icons/hicolor/32x32/apps/wicd-gtk.png
/usr/share/icons/hicolor/36x36/apps/wicd-gtk.png
/usr/share/icons/hicolor/48x48/apps/wicd-gtk.png
/usr/share/icons/hicolor/64x64/apps/wicd-gtk.png
/usr/share/icons/hicolor/72x72/apps/wicd-gtk.png
/usr/share/icons/hicolor/96x96/apps/wicd-gtk.png
/usr/share/icons/hicolor/scalable/apps/wicd-gtk.svg
/usr/share/man/man1/wicd-client.1
/usr/share/man/man5/wicd-manager-settings.conf.5
/usr/share/man/man5/wicd-wired-settings.conf.5
/usr/share/man/man5/wicd-wireless-settings.conf.5
/usr/share/man/man8/wicd-cli.8
/usr/share/man/man8/wicd-curses.8
/usr/share/man/man8/wicd.8
/usr/share/man/nl/man1/wicd-client.1
/usr/share/man/nl/man5/wicd-manager-settings.conf.5
/usr/share/man/nl/man5/wicd-wired-settings.conf.5
/usr/share/man/nl/man5/wicd-wireless-settings.conf.5
/usr/share/man/nl/man8/wicd-curses.8
/usr/share/man/nl/man8/wicd.8
/usr/share/pixmaps/wicd
/usr/share/pixmaps/wicd-gtk.xpm
/usr/share/pixmaps/wicd/bad-signal-lock.png
/usr/share/pixmaps/wicd/bad-signal.png
/usr/share/pixmaps/wicd/both-bad-signal-lock.png
/usr/share/pixmaps/wicd/both-bad-signal.png
/usr/share/pixmaps/wicd/both-good-signal-lock.png
/usr/share/pixmaps/wicd/both-good-signal.png
/usr/share/pixmaps/wicd/both-high-signal-lock.png
/usr/share/pixmaps/wicd/both-high-signal.png
/usr/share/pixmaps/wicd/both-low-signal-lock.png
/usr/share/pixmaps/wicd/both-low-signal.png
/usr/share/pixmaps/wicd/good-signal-lock.png
/usr/share/pixmaps/wicd/good-signal.png
/usr/share/pixmaps/wicd/high-signal-lock.png
/usr/share/pixmaps/wicd/high-signal.png
/usr/share/pixmaps/wicd/idle-bad-signal-lock.png
/usr/share/pixmaps/wicd/idle-bad-signal.png
/usr/share/pixmaps/wicd/idle-good-signal-lock.png
/usr/share/pixmaps/wicd/idle-good-signal.png
/usr/share/pixmaps/wicd/idle-high-signal-lock.png
/usr/share/pixmaps/wicd/idle-high-signal.png
/usr/share/pixmaps/wicd/idle-low-signal-lock.png
/usr/share/pixmaps/wicd/idle-low-signal.png
/usr/share/pixmaps/wicd/low-signal-lock.png
/usr/share/pixmaps/wicd/low-signal.png
/usr/share/pixmaps/wicd/no-signal.png
/usr/share/pixmaps/wicd/receiving-bad-signal-lock.png
/usr/share/pixmaps/wicd/receiving-bad-signal.png
/usr/share/pixmaps/wicd/receiving-good-signal-lock.png
/usr/share/pixmaps/wicd/receiving-good-signal.png
/usr/share/pixmaps/wicd/receiving-high-signal-lock.png
/usr/share/pixmaps/wicd/receiving-high-signal.png
/usr/share/pixmaps/wicd/receiving-low-signal-lock.png
/usr/share/pixmaps/wicd/receiving-low-signal.png
/usr/share/pixmaps/wicd/signal-100.png
/usr/share/pixmaps/wicd/signal-25.png
/usr/share/pixmaps/wicd/signal-50.png
/usr/share/pixmaps/wicd/signal-75.png
/usr/share/pixmaps/wicd/transmitting-bad-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-bad-signal.png
/usr/share/pixmaps/wicd/transmitting-good-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-good-signal.png
/usr/share/pixmaps/wicd/transmitting-high-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-high-signal.png
/usr/share/pixmaps/wicd/transmitting-low-signal-lock.png
/usr/share/pixmaps/wicd/transmitting-low-signal.png
/usr/share/pixmaps/wicd/wired-gui.svg
/usr/share/pixmaps/wicd/wired.png
/usr/share/wicd/cli
/usr/share/wicd/curses
/usr/share/wicd/gtk
/usr/share/wicd/cli/wicd-cli.py
/usr/share/wicd/curses/configscript_curses.py
/usr/share/wicd/curses/curses_misc.py
/usr/share/wicd/curses/netentry_curses.py
/usr/share/wicd/curses/prefs_curses.py
/usr/share/wicd/curses/wicd-curses.py
/usr/share/wicd/gtk/configscript.py
/usr/share/wicd/gtk/gui.py
/usr/share/wicd/gtk/guiutil.py
/usr/share/wicd/gtk/netentry.py
/usr/share/wicd/gtk/prefs.py
/usr/share/wicd/gtk/wicd-client.py
/usr/share/wicd/gtk/wicd.glade
/var/cache/apt/archives/python-wicd_1.7.0+ds1-6_all.deb
/var/cache/apt/archives/wicd-daemon_1.7.0+ds1-6_all.deb
/var/cache/apt/archives/wicd-kde_0.2.1-4_i386.deb
/var/lib/update-rc.d/wicd
kris@kris:~$ 
/CODE]

---

### Post by KrisB on 2011-08-01
restarted just to see and it's still doing it.  :(

---

### Post by nipennem on 2011-08-01
> **KrisB said:**
> ok I did, thanks! Should I restart and see if that fixed it?

```


/usr/share/applications/wicd.desktop
/usr/share/autostart/wicd-tray.desktop
/usr/share/icons/hicolor/128x128/apps/wicd-gtk.png
/usr/share/icons/hicolor/16x16/apps/wicd-gtk.png
/usr/share/icons/hicolor/192x192/apps/wicd-gtk.png
/usr/share/icons/hicolor/22x22/apps/wicd-gtk.png
/usr/share/icons/hicolor/24x24/apps/wicd-gtk.png
/usr/share/icons/hicolor/32x32/apps/wicd-gtk.png
/usr/share/icons/hicolor/36x36/apps/wicd-gtk.png
/usr/share/icons/hicolor/48x48/apps/wicd-gtk.png
/usr/share/icons/hicolor/64x64/apps/wicd-gtk.png
/usr/share/icons/hicolor/72x72/apps/wicd-gtk.png
/usr/share/icons/hicolor/96x96/apps/wicd-gtk.png
/usr/share/icons/hicolor/scalable/apps/wicd-gtk.svg
/usr/share/man/man1/wicd-client.1
/usr/share/man/man5/wicd-manager-settings.conf.5
/usr/share/man/man5/wicd-wired-settings.conf.5
/usr/share/man/man5/wicd-wireless-settings.conf.5
/usr/share/man/man8/wicd-cli.8
/usr/share/man/man8/wicd-curses.8
/usr/share/man/man8/wicd.8
/usr/share/man/nl/man1/wicd-client.1
/usr/share/man/nl/man5/wicd-manager-settings.conf.5
/usr/share/man/nl/man5/wicd-wired-settings.conf.5
/usr/share/man/nl/man5/wicd-wireless-settings.conf.5
/usr/share/man/nl/man8/wicd-curses.8
/usr/share/man/nl/man8/wicd.8
kris@kris:~$ 
/CODE]


I have a suspicion you 

(1) installed wicd through package management
(2) ALSO manually installed wicd through "./configure","make","make install"

because the sources are in your home directory and your system is still full of wicd files.

The problem with (2) is that there is no such option as "make uninstall", at least not that I know of, and wicd has been installed to your system manually, so must be taken out manually.

If you feel adventurous, which most certainly you do, you can try the following at your own risk -- I am not responsible for the consequences and you might badly break your system (it looks like removing everything from the list you posted but it's not -- DO NOT touch app-install or apt/dpkg folders).

[CODE]
rm -rf /home/kris/wicd-1.7.0 /usr/share/wicd /usr/share/doc/wicd  /usr/local/lib/python2.7/dist-packages/wicd  /usr/share/pixmaps/wicd /var/lib/update-rc.d/wicd
rm /usr/bin/wicd-cli /usr/bin/wicd-client /usr/bin/wicd-curses /usr/bin/wicd-gtk /usr/share/applications/wicd.desktop /usr/share/autostart/wicd-tray.desktop /usr/share/icons/hicolor/128x128/apps/wicd-gtk.png /usr/share/icons/hicolor/16x16/apps/wicd-gtk.png /usr/share/icons/hicolor/192x192/apps/wicd-gtk.png /usr/share/icons/hicolor/22x22/apps/wicd-gtk.png /usr/share/icons/hicolor/24x24/apps/wicd-gtk.png /usr/share/icons/hicolor/32x32/apps/wicd-gtk.png /usr/share/icons/hicolor/36x36/apps/wicd-gtk.png /usr/share/icons/hicolor/48x48/apps/wicd-gtk.png /usr/share/icons/hicolor/64x64/apps/wicd-gtk.png /usr/share/icons/hicolor/72x72/apps/wicd-gtk.png /usr/share/icons/hicolor/96x96/apps/wicd-gtk.png /usr/share/icons/hicolor/scalable/apps/wicd-gtk.svg /usr/share/man/man1/wicd-client.1 /usr/share/man/man5/wicd-manager-settings.conf.5 /usr/share/man/man5/wicd-wired-settings.conf.5 /usr/share/man/man5/wicd-wireless-settings.conf.5 /usr/share/man/man8/wicd-cli.8 /usr/share/man/man8/wicd-curses.8 /usr/share/man/man8/wicd.8 /usr/share/man/nl/man1/wicd-client.1 /usr/share/man/nl/man5/wicd-manager-settings.conf.5 /usr/share/man/nl/man5/wicd-wired-settings.conf.5 /usr/share/man/nl/man5/wicd-wireless-settings.conf.5 /usr/share/man/nl/man8/wicd-curses.8 /usr/share/man/nl/man8/wicd.8


```When done, redo sudo updatedb etc. and repost output.

You will need sudo to remove ... I deliberately left it out to avoid you just copy/paste without reading the disclaimer.

---

### Post by KrisB on 2011-08-01
yes- you're right- did that with help when I couldn't get the wireless working.  not sure why the error stopped for a bit then started again.  I'm not sure I want to risk it, but maybe it's worth it.  I've had nothing but problems since using 11.04.  I hope it won't break it.  :(  I'll think about it before I try it.

---

### Post by nipennem on 2011-08-01
> **KrisB said:**
> yes- you're right- did that with help when I couldn't get the wireless working.  not sure why the error stopped for a bit then started again.  I'm not sure I want to risk it, but maybe it's worth it.  I've had nothing but problems since using 11.04.  I hope it won't break it.  :(  I'll think about it before I try it.

Basically I've checked with my system and used common sense to see what files with "wicd" in them are there.
Most of them are not.

There is no guarantee, however, that the wicd installation added files in paths which do not contain 'wicd'. Ideally, when you manually install software, you should put it in /opt.

When they have configure scripts, this is typically done by passing a --prefix argument to the configure script, e.g.

```
./configure --prefix=/opt/wicd other-options-here
```

This would have saved you a lot of trouble.

Another thing you *COULD* try, not guaranteed to work, is to

- INSTALL the Ubuntu wicd packages -- all of them
- "sudo dpkg --purge .." all of them
- check if the files are gone :)
This might be the safe way, although it will probably make you remove networkmanager when installing wicd, and force you to switch back when purging wicd. Not sure on that one.

---

### Post by KrisB on 2011-08-01
When I originally tried it b/c network manager was working only partially, I tried wicd and wi-fi radar unsucessfully and wound up with NO  internet.   Makes me nervous about trying that b/c at least right now it connects.  (after a whole day of help from that forum).  wish I understood command line better.  I'm a little scared to mess with it.

---

### Post by KrisB on 2011-08-01
any second opinions? Will that break it? Thoughts before I try it?

---

### Post by bruno9779 on 2011-08-01
There is a "make uninstall" command. It is not used very often, but it is worth a try:
```

cd /home/kris/wicd-1.7.0
sudo make uninstall
```

Then go ahead and remove the files as suggested above.

EDIT:

Assuming you downloaded the source from here [https://sourceforge.net/projects/wicd/files/wicd-stable/wicd-1.7.0/wicd-1.7.0.tar.gz/download](https://sourceforge.net/projects/wicd/files/wicd-stable/wicd-1.7.0/wicd-1.7.0.tar.gz/download)
There is an uninstall.sh script in the source. Run that and remove the wicd files left in your home folder.

---

### Post by nipennem on 2011-08-02
> **bruno9779 said:**
> There is a "make uninstall" command. It is not used very often, but it is worth a try:
```

cd /home/kris/wicd-1.7.0
sudo make uninstall
```Then go ahead and remove the files as suggested above.

EDIT:

Assuming you downloaded the source from here [https://sourceforge.net/projects/wicd/files/wicd-stable/wicd-1.7.0/wicd-1.7.0.tar.gz/download](https://sourceforge.net/projects/wicd/files/wicd-stable/wicd-1.7.0/wicd-1.7.0.tar.gz/download)
There is an uninstall.sh script in the source. Run that and remove the wicd files left in your home folder.

Cool, didn't know this... ! I don't think it's a common practice.

---

