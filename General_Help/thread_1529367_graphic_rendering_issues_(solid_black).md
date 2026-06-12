---
title: "graphic rendering issues (solid black)"
date: 2010-07-12
forum: General Help
---

### Post by veehexx on 2010-07-12
I'm having similar issues with 2 programs.

firstly is the 'Terminal Server Client', and connecting to server 2008r2. im using the RDPv5 profile. the mouse cursor correctly changes it's style to the windows one, but it's solid black in colour.

on a similar note, im using 'fox splitter' addon in firefox, and the bars at the edge of screen are also solid black in colour.

operationally, both work fine, just their colours are incorrect.

i'm running nvidia 8800gtx in twinview on version 195.36.24, ubuntu 10.04-x64

although I experience this same issue on intel based gfx laptop, previous versions of ubuntu, and on both x86 and x64 releases...so it's either an ongoing bug, or some default setting I need to change somewhere...

---

### Post by dino99 on 2010-07-12
its time to hunt usefull errors logged either into:

- .xsession-errors (/home, ctrl+h to unhide)
- system admin logviewer

---

### Post by veehexx on 2010-07-13
since im not entirely sure what im looking for, heres my log....

> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_GB.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_CONTROL=/tmp/keyring-2xs1KG
GNOME_KEYRING_CONTROL=/tmp/keyring-2xs1KG
SSH_AUTH_SOCK=/tmp/keyring-2xs1KG/ssh
GNOME_KEYRING_CONTROL=/tmp/keyring-2xs1KG
SSH_AUTH_SOCK=/tmp/keyring-2xs1KG/ssh

(polkit-gnome-authentication-agent-1:1448): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:1448): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(gnome-power-manager:1453): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.24.1/gobject/gsignal.c:2273: signal `proxy-status' is invalid for instance `0x19b45d0'
** (nm-applet:1458): DEBUG: old state indicates that this was not a disconnect 0
Unable to find a synaptics device.
Starting gtk-window-decorator
Initializing nautilus-gdu extension
I/O warning : failed to load external entity "/home/tim/.compiz/session/105ae7ca7496e765c0127901157840866700000013810027"
VLC media player 1.0.6 Goldeneye
[0x12974b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x16dd528] access_http access: Raw-audio server found, mp3 demuxer selected
[0x16c5ff8] pulse audio output: No. of Audio Channels: 2
evolution-alarm-notify-Message: Setting timeout for 50390 1279062000 1279011610
evolution-alarm-notify-Message:  Wed Jul 14 00:00:00 2010

evolution-alarm-notify-Message:  Tue Jul 13 10:00:10 2010

evolution-alarm-notify-Message: Setting timeout for 12287 1279023900 1279011613
evolution-alarm-notify-Message:  Tue Jul 13 13:25:00 2010

evolution-alarm-notify-Message:  Tue Jul 13 10:00:13 2010

VLC media player 1.0.6 Goldeneye
[0x22b74b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x26f00e8] access_http access: Raw-audio server found, mp3 demuxer selected
[0x7f1934014568] pulse audio output: No. of Audio Channels: 2
** (update-notifier:1652): DEBUG: Skipping reboot required
VLC media player 1.0.6 Goldeneye
[0x24204b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x2845808] access_http access: Raw-audio server found, mp3 demuxer selected
[0x287eac8] pulse audio output: No. of Audio Channels: 2
VLC media player 1.0.6 Goldeneye
[0xc2b4b8] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x1c63fb8] access_http access: Raw-audio server found, mp3 demuxer selected
[0x108e718] pulse audio output: No. of Audio Channels: 2
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Autoselected keyboard map en-gb

the very last line (Autoselected...) is when Terminal Server Client is ran and logged on. and yes, it is short because i purged it prior to a reboot and retest :)

---

