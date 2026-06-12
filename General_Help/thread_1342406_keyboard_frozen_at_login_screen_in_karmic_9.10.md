---
title: "keyboard frozen at login screen in karmic 9.10"
date: 2009-11-30
forum: General Help
---

### Post by hart02 on 2009-11-30
After reinstalling my os from another issue again,My system now has a frozen keyboard at startup but the mouse works. It is a PS/2 Keyboard and mouse.I cannot find any useful information to help me fix this.I have tried the autologin to see if i could find options or apps that are messing with the keyboard with no luck.I cant figure out how i can change which desktop i autologin to. I got xfce on my system and it logs in to that by default. I think that gnome could have some accessibility options on that could be keeping the keyboard from working.But I can't access those settings from xfce. Can't find the .xsession file in my home directory and i don't konw the syntax for the .xsession file. I will post the content of some files that might help debug this.

**My .xsession-errors file**
```
/etc/gdm/Xsession: Beginning session setup...
export DESKTOP_SESSION='default'
export DISPLAY=':0'
export GDMSESSION='default'
export GDM_KEYBOARD_LAYOUT='us'
export GDM_LANG='en_US.UTF-8'
export HOME='/home/brian'
export LANG='en_US.UTF-8'
export LOGNAME='brian'
export PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
export PWD='/home/brian'
export SHELL='/bin/bash'
export SPEECHD_PORT='7560'
export USER='brian'
export USERNAME='brian'
export XAUTHORITY='/var/run/gdm/auth-for-brian-t5AH9K/database'
export XDG_SESSION_COOKIE='fc9696983544f8d8e642df5c4b10cb00-1259619059.455510-491433618'
MainThread 2009/11/30 17:11:02.1974 (sabayon-apply): No profile for user 'brian' found
No profile for user 'brian' found
MainThread 2009/11/30 17:11:02.1976 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2009/11/30 17:11:02.1978 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 100, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== BEGIN MILESTONES (/usr/sbin/sabayon-apply) =====
MainThread 2009/11/30 17:11:02.1974 (sabayon-apply): No profile for user 'brian' found
MainThread 2009/11/30 17:11:02.1976 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2009/11/30 17:11:02.1978 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 100, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END MILESTONES (/usr/sbin/sabayon-apply) =====
===== BEGIN RING BUFFER (/usr/sbin/sabayon-apply) =====
MainThread 2009/11/30 17:11:02.1974 (sabayon-apply): No profile for user 'brian' found
MainThread 2009/11/30 17:11:02.1976 (sabayon-apply): Fatal exception!  Exiting abnormally.
MainThread 2009/11/30 17:11:02.1978 (sabayon-apply): Traceback (most recent call last):
  File "/usr/sbin/sabayon-apply", line 100, in <module>
    sys.exit (util.EXIT_CODE_NO_USER_PROFILE)
SystemExit: 3

===== END RING BUFFER (/usr/sbin/sabayon-apply) =====


This configuration for the debug log can be re-created
by putting the following in ~/sabayon-debug-log.conf
(use ';' to separate domain names):

[debug log]
max lines = 1000
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xscreensaver: 17:11:02: already running on display :0.0 (window 0x400001)
 from process 4236 (brian@bmanspc).
xscreensaver: 17:11:02: already running on display :0.0 (window 0x400005)
 from process 4236 (brian@bmanspc).
xfdesktop[5403]: starting up

(xfce4-mixer-plugin:5441): libxfce4mixer-CRITICAL **: xfce_mixer_get_track: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:5441): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_card: assertion `GST_IS_MIXER (card)' failed

(xfce4-mixer-plugin:5441): xfce4-mixer-plugin-CRITICAL **: xfce_mixer_plugin_set_track: assertion `GST_IS_MIXER_TRACK (track)' failed
no maximize: false
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600145
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600144
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260014d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260014c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260015d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260015c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600165
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600164
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600149
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600148
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600161
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600160
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600151
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600150
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600159
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600158
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600171
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600170
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600185
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600184
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260019d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260019c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001a5
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001a4
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001b5
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001b4
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001bd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001bc
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001a1
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001a0
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001b9
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001b8
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001a9
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001a8
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001b1
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001b0
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001c7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001c6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001cf
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001ce
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001df
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001de
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001e7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001e6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001cb
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001ca
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001e3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001e2
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001d3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001d2
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001db
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001da
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001f4
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001f3
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001fc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001fb
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600214
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600213
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260021c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260021b
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26001f8
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001f7
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600218
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600217
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600200
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26001ff
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600206
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600205
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600210
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260020f
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600229
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600228
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600231
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600230
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600249
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600248
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600251
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600250
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260022d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260022c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260024d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260024c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600235
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600234
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260023b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260023a
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600245
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600244
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260025e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260025d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600266
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600265
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260027e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260027d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600286
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600285
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600262
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600261
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600282
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600281
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260026a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600269
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600270
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260026f
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260027a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600279
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600293
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600292
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260029b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260029a
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002b3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002b2
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002bb
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002ba
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600297
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600296
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002b7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002b6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260029f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260029e
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002a5
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002a4
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002af
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002ae
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002c8
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002c7
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002d0
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002cf
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002e8
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002e7
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002f0
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002ef
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002cc
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002cb
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002ec
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002eb
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002d4
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002d3
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002da
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002d9
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002e4
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002e3
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26002fd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26002fc
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600305
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600304
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260031d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260031c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600325
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600324
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600301
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600300
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600321
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600320
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600309
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600308
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260030f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260030e
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600319
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600318
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600332
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600331
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260033a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600339
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600352
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600351
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260035a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600359
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600336
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600335
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600356
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600355
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260033e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260033d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600344
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600343
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260034e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260034d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600367
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600366
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260036f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260036e
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600387
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600386
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260038f
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260038e
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260036b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260036a
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260038b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260038a
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600373
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600372
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600379
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600378
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600383
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600382
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003b5
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003b4
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003cd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003cc
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003c9
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003c8
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003e2
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003e1
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600402
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600401
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003fe
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003fd
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003e6
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003e5
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26003ec
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26003eb
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600417
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600416
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600437
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600436
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600433
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600432
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260041b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260041a
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600421
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600420
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600439
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600438
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600440
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260043f
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600447
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600446
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260044e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260044d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600455
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600454
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260045c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260045b
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600460
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260045f
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600467
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600466
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260046e
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260046d
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600475
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600474
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260047c
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260047b
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600480
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260047f
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600484
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600483
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600497
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600496
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004a7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004a6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004ab
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004aa
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004b9
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004b8
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004bf
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004be
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004c3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004c2
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004cd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004cc
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004d3
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004d2
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004d7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004d6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004e1
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004e0
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004e7
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004e6
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004eb
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004ea
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004f9
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004f8
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x26004ff
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x26004fe
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600503
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600502
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260050d
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260050c
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600513
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600512
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600517
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600516
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600521
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600520
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x2600527
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x2600526
X Error: RenderBadPicture (invalid Picture parameter) 172
  Extension:    152 (RENDER)
  Minor opcode: 7 (RenderFreePicture)
  Resource id:  0x260052b
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode: 54 (X_FreePixmap)
  Resource id:  0x260052a
30/11/2009 05:11:16 PM passing arg to libvncserver: -rfbport
30/11/2009 05:11:16 PM passing arg to libvncserver: 5900
30/11/2009 05:11:16 PM x11vnc version: 0.9.4 lastmod: 2008-06-24
30/11/2009 05:11:16 PM Using X display :0.0
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM ------------------ USEFUL INFORMATION ------------------
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM Wireframing: -wireframe mode is in effect for window moves.
30/11/2009 05:11:16 PM   If this yields undesired behavior (poor response, painting
30/11/2009 05:11:16 PM   errors, etc) it may be disabled:
30/11/2009 05:11:16 PM    - use '-nowf' to disable wireframing completely.
30/11/2009 05:11:16 PM    - use '-nowcr' to disable the Copy Rectangle after the
30/11/2009 05:11:16 PM      moved window is released in the new position.
30/11/2009 05:11:16 PM   Also see the -help entry for tuning parameters.
30/11/2009 05:11:16 PM   You can press 3 Alt_L's (Left "Alt" key) in a row to 
30/11/2009 05:11:16 PM   repaint the screen, also see the -fixscreen option for
30/11/2009 05:11:16 PM   periodic repaints.
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM XFIXES available on display, resetting cursor mode
30/11/2009 05:11:16 PM   to: '-cursor most'.
30/11/2009 05:11:16 PM   to disable this behavior use: '-cursor arrow'
30/11/2009 05:11:16 PM   or '-noxfixes'.
30/11/2009 05:11:16 PM using XFIXES for cursor drawing.
30/11/2009 05:11:16 PM GrabServer control via XTEST.
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM Scroll Detection: -scrollcopyrect mode is in effect to
30/11/2009 05:11:16 PM   use RECORD extension to try to detect scrolling windows
30/11/2009 05:11:16 PM   (induced by either user keystroke or mouse input).
30/11/2009 05:11:16 PM   If this yields undesired behavior (poor response, painting
30/11/2009 05:11:16 PM   errors, etc) it may be disabled via: '-noscr'
30/11/2009 05:11:16 PM   Also see the -help entry for tuning parameters.
30/11/2009 05:11:16 PM   You can press 3 Alt_L's (Left "Alt" key) in a row to 
30/11/2009 05:11:16 PM   repaint the screen, also see the -fixscreen option for
30/11/2009 05:11:16 PM   periodic repaints.
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM XKEYBOARD: number of keysyms per keycode 6 is greater
30/11/2009 05:11:16 PM   than 4 and 288 keysyms are mapped above 4.
30/11/2009 05:11:16 PM   Automatically switching to -xkb mode.
30/11/2009 05:11:16 PM   If this makes the key mapping worse you can
30/11/2009 05:11:16 PM   disable it with the "-noxkb" option.
30/11/2009 05:11:16 PM   Also, remember "-remap DEAD" for accenting characters.
30/11/2009 05:11:16 PM X FBPM extension not supported.
30/11/2009 05:11:16 PM X display is capable of DPMS.
30/11/2009 05:11:16 PM --------------------------------------------------------
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM Default visual ID: 0x21
30/11/2009 05:11:16 PM Read initial data from X display into framebuffer.
30/11/2009 05:11:16 PM initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/10240
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM X display :0.0 is 32bpp depth=24 true color
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM Listening for VNC connections on TCP port 5900
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM Xinerama is present and active (e.g. multi-head).
30/11/2009 05:11:16 PM Xinerama: enabling -xwarppointer mode to try to correct
30/11/2009 05:11:16 PM Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
30/11/2009 05:11:16 PM Xinerama: Use -noxwarppointer to force XTEST.
30/11/2009 05:11:16 PM Xinerama: no blackouts needed (screen fills rectangle)
30/11/2009 05:11:16 PM 
30/11/2009 05:11:16 PM fb read rate: 454 MB/sec
30/11/2009 05:11:16 PM fast read: reset wait  ms to: 10
30/11/2009 05:11:16 PM fast read: reset defer ms to: 15
30/11/2009 05:11:16 PM screen setup finished.
30/11/2009 05:11:16 PM 

The VNC desktop is:      bmanspc:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified
tput: No value for $TERM and no -T specified

(polkit-gnome-authentication-agent-1:5567): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:5567): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: adding killswitch idx 0 state 1
** Message: Reading of RFKILL events failed
** Message: killswitch 0 is 1
** Message: killswitches state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1
(netbook-launcher:5577): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:5577): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:5577): libnetbook-launcher-DEBUG: CONFIG: Font changed: Sans 10

(netbook-launcher:5577): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting

System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.ExtensionNodeEventArgs.get_ExtensionObject () [0x00000] 
  at Do.Platform.Services.OnServiceChanged (System.Object sender, Mono.Addins.ExtensionNodeEventArgs e) [0x00000] 
  at Mono.Addins.ExtensionNode.add_ExtensionNodeChanged (Mono.Addins.ExtensionNodeEventHandler value) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
[Fatal 17:11:25.563] [Services] Service of type INetworkService not found. Using default service instead.
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 

(Do:5548): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Could not locate Tomboy on D-Bus. Perhaps it's not running?
Error while getting object for node in path '/Do/Service'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Platform.Linux.NetworkService.get_State () [0x00000] 
  at Do.Platform.Linux.NetworkService.SetConnected () [0x00000] 
  at Do.Platform.Linux.NetworkService..ctor () [0x00000] 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at System.Activator.CreateInstance (System.Type type) [0x00000] 
  at Mono.Addins.TypeExtensionNode.CreateInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance () [0x00000] 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) [0x00000] 
  at Mono.Addins.ExtensionNode.GetChildObjects (System.Type arrayElementType, Boolean reuseCachedInstance) [0x00000] 
Has notifications support True
rename failed
Loading...
Connecting to daemon...
Can't connect to the daemon, trying to start it automatically...
Wicd daemon is shutting down!
Done loading.
Traceback (most recent call last):
  File "/usr/share/wicd/wicd-client.py", line 88, in wrapper
    return func(*args, **kwargs)
  File "/usr/share/wicd/wicd-client.py", line 546, in _trigger_scan_if_needed
    wireless.Scan(False)
AttributeError: 'NoneType' object has no attribute 'Scan'
(netbook-launcher:5577): liblauncher-DEBUG: launcher-menu.c:361

(netbook-launcher:5577): GLib-CRITICAL **: g_str_has_suffix: assertion `str != NULL' failed
ORPHAN: Ubuntu Software Center
(netbook-launcher:5577): liblauncher-DEBUG: Workarea: (0, 25) (0, 25)
/var/crash/libindi0
** (maximus:5460): DEBUG: Window opened: res_name=Alacarte -- class_name=alacarte
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 436, in on_item_tree_show_toggled
    self.editor.setVisible(item, True)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 201, in setVisible
    menu_xml = self.__getXmlMenu(self.__getPath(item.get_parent()), dom, dom)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 481, in __getPath
    path = menu.tree.root.get_menu_id()
AttributeError: 'NoneType' object has no attribute 'root'
Use of uninitialized value $Keypress::identity in concatenation (.) or string at /usr/share/perl5/Keypress.pm line 85, <READ> line 37.
Use of uninitialized value in subroutine entry at /usr/bin/keypress-ui line 138, <DATA> line 1.
Use of uninitialized value $total_overtime in concatenation (.) or string at /usr/bin/keypress-ui line 315, <READ> line 104.
** (maximus:5460): DEBUG: Window opened: res_name=Keypress-ui -- class_name=keypress-ui
*** glibc detected *** /usr/bin/Terminal: free(): invalid pointer: 0x065dde58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0x73fff1]
/lib/tls/i686/cmov/libc.so.6[0x7416f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x74479d]
/usr/lib/tls/libnvidia-tls.so.1[0x159b00]
/usr/lib/libgnustep-gui.so.0.16[0x24f300]
/usr/lib/libgnustep-gui.so.0.16[0x2463e0]
/usr/lib/libgnustep-gui.so.0.16[0x2d7008]
/usr/lib/libgnustep-gui.so.0.16[0x2d4144]
/usr/lib/libgnustep-gui.so.0.16[0x2d23f1]
/usr/lib/libgnustep-gui.so.0.16[0x2d2639]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x37a66d6]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x37a6b71]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x37a7402]
/usr/lib/libgnustep-gui.so.0.16[0x3b0144]
/usr/lib/libgnustep-gui.so.0.16[0x3b0b9f]
/usr/lib/libgnustep-gui.so.0.16[0x2376a9]
/usr/lib/libgnustep-gui.so.0.16[0x22fb2c]
/usr/lib/libgnustep-gui.so.0.16[0x231836]
/usr/bin/Terminal(main+0x130)[0x804d330]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x6ebb56]
/usr/bin/Terminal[0x804aa41]
======= Memory map: ========
00110000-00125000 r-xp 00000000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
00125000-00126000 r--p 00014000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
00126000-00127000 rw-p 00015000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
00127000-00129000 rw-p 00000000 00:00 0 
00129000-0013f000 r-xp 00000000 08:01 102127     /usr/lib/libobjc.so.2.0.0
0013f000-00140000 r--p 00015000 08:01 102127     /usr/lib/libobjc.so.2.0.0
00140000-00142000 rw-p 00016000 08:01 102127     /usr/lib/libobjc.so.2.0.0
00142000-00143000 rw-p 00000000 00:00 0 
00143000-0014a000 r-xp 00000000 08:01 2755       /usr/lib/libgif.so.4.1.6
0014a000-0014b000 r--p 00006000 08:01 2755       /usr/lib/libgif.so.4.1.6
0014b000-0014c000 rw-p 00007000 08:01 2755       /usr/lib/libgif.so.4.1.6
0014c000-00153000 r-xp 00000000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
00153000-00154000 r--p 00006000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
00154000-00155000 rw-p 00007000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
00155000-00157000 r-xp 00000000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00157000-00158000 r--p 00001000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00158000-00159000 rw-p 00002000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00159000-0015a000 r-xp 00000000 08:01 1216806    /usr/lib/tls/libnvidia-tls.so.195.22
0015a000-0015b000 rw-p 00000000 08:01 1216806    /usr/lib/tls/libnvidia-tls.so.195.22
0015c000-00177000 r-xp 00000000 08:01 521        /lib/ld-2.10.1.so
00177000-00178000 r--p 0001a000 08:01 521        /lib/ld-2.10.1.so
00178000-00179000 rw-p 0001b000 08:01 521        /lib/ld-2.10.1.so
00179000-004b2000 r-xp 00000000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
004b2000-004b3000 r--p 00339000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
004b3000-0058f000 rw-p 0033a000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
0058f000-00590000 rw-p 00000000 00:00 0 
00590000-005b4000 r-xp 00000000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
005b4000-005b5000 r--p 00023000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
005b5000-005b6000 rw-p 00024000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
005b6000-005d2000 r-xp 00000000 08:01 571        /lib/libgcc_s.so.1
005d2000-005d3000 r--p 0001b000 08:01 571        /lib/libgcc_s.so.1
005d3000-005d4000 rw-p 0001c000 08:01 571        /lib/libgcc_s.so.1
005d4000-005fa000 r-xp 00000000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
005fa000-005fb000 ---p 00026000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
005fb000-005fc000 r--p 00026000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
005fc000-005fe000 rw-p 00027000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
005fe000-0069c000 r-xp 00000000 08:01 2470       /usr/lib/libaspell.so.15.1.4
0069c000-0069f000 r--p 0009e000 08:01 2470       /usr/lib/libaspell.so.15.1.4
0069f000-006a0000 rw-p 000a1000 08:01 2470       /usr/lib/libaspell.so.15.1.4
006a0000-006a4000 rw-p 00000000 00:00 0 
006a4000-006ca000 r-xp 00000000 08:01 32038      /usr/lib/libpng12.so.0.39.0
006ca000-006cb000 r--p 00025000 08:01 32038      /usr/lib/libpng12.so.0.39.0
006cb000-006cc000 rw-p 00026000 08:01 32038      /usr/lib/libpng12.so.0.39.0
006cc000-006cf000 r-xp 00000000 08:01 577        /lib/libgpg-error.so.0.4.0
006cf000-006d0000 r--p 00002000 08:01 577        /lib/libgpg-error.so.0.4.0
006d0000-006d1000 rw-p 00003000 08:01 577        /lib/libgpg-error.so.0.4.0
006d1000-006d3000 r-xp 00000000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
006d3000-006d4000 r--p 00001000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
006d4000-006d5000 rw-p 00002000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
006d5000-00813000 r-xp 00000000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00813000-00815000 r--p 0013e000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00815000-00816000 rw-p 00140000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00816000-00819000 rw-p 00000000 00:00 0 
00819000-0081e000 r-xp 00000000 08:01 2686       /usr/lib/libffi.so.5.0.8
0081e000-0081f000 ---p 00005000 08:01 2686       /usr/lib/libffi.so.5.0.8
0081f000-00820000 r--p 00005000 08:01 2686       /usr/lib/libffi.so.5.0.8
00820000-00821000 rw-p 00006000 08:01 2686       /usr/lib/libffi.so.5.0.8
00821000-00823000 r-xp 00000000 08:01 524899     /usr/lib/gconv/UTF-16.so
00823000-00824000 r--p 00001000 08:01 524899     /usr/lib/gconv/UTF-16.so
00824000-00825000 rw-p 00002000 08:01 524899     /usr/lib/gconv/UTF-16.so
00827000-00828000 r-xp 00000000 00:00 0          [vdso]
00828000-00885000 r-xp 00000000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00885000-00887000 r--p 0005c000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00887000-00888000 rw-p 0005e000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00888000-0089b000 r-xp 00000000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
0089b000-0089c000 r--p 00012000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
0089c000-0089d000 rw-p 00013000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
0089d000-0089f000 rw-p 00000000 00:00 0 
0089f000-008a6000 r-xp 00000000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
008a6000-008a7000 r--p 00006000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
008a7000-008a8000 rw-p 00007000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
008a8000-008bc000 r-xp 00000000 08:01 673        /lib/libz.so.1.2.3.3
008bc000-008bd000 r--p 00013000 08:01 673        /lib/libz.so.1.2.3.3
008bd000-008be000 rw-p 00014000 08:01 673        /lib/libz.so.1.2.3.3
008be000-008de000 r-xp 00000000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
008de000-008df000 r--p 0001f000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
008df000-008e0000 rw-p 00020000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
008e0000-00983000 r-xp 00000000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00983000-00987000 r--p 000a2000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00987000-00988000 rw-p 000a6000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00988000-009bd000 r-xp 00000000 08:01 3430       /usr/lib/libxslt.so.1.1.24
009bd000-009be000 r--p 00034000 08:01 3430       /usr/lib/libxslt.so.1.1.24
009be000-009bf000 rw-p 00035000 08:01 3430       /usr/lib/libxslt.so.1.1.24
009bf000-009cd000 r-xp 00000000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
009cd000-009ce000 ---p 0000e000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
009ce000-009cf000 r--p 0000e000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
009cf000-009d0000 rw-p 0000f000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
009d0000-00a07000 r-xp 00000000 08:01 557        /lib/libdbus-1.so.3.4.0
00a07000-00a08000 r--p 00036000 08:01 557        /lib/libdbus-1.so.3.4.0
00a08000-00a09000 rw-p 00037000 08:01 557        /lib/libdbus-1.so.3.4.0
00a09000-00a13000 r-xp 00000000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00a13000-00a14000 r--p 00009000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00a14000-00a15000 rw-p 0000a000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00a15000-00a25000 r-xp 00000000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00a25000-00a26000 r--p 0000f000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00a26000-00a27000 rw-p 00010000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00a2a000-00dac000 r-xp 00000000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
00dac000-00dad000 r--p 00382000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
00dad000-00e32000 rw-p 00383000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
00e32000-00e33000 rw-p 00000000 00:00 0 
00e33000-00f55000 r-xp 00000000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00f55000-00f56000 ---p 00122000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00f56000-00f5a000 r--p 00122000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00f5a000-00f5b000 rw-p 00126000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00f5b000-00f5c000 rw-p 00000000 00:00 0 
00f5c000-01042000 r-xp 00000000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
01042000-01046000 r--p 000e6000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
01046000-01047000 rw-p 000ea000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
01047000-0104e000 rw-p 00000000 00:00 0 
011d7000-011da000 r-xp 00000000 08:01 666        /lib/libuuid.so.1.3.0
011da000-011db000 r--p 00002000 08:01 666        /lib/libuuid.so.1.3.0
011db000-011dc000 rw-p 00003000 08:01 666        /lib/libuuid.so.1.3.0
015c6000-015d0000 r-xp 00000000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
015d0000-015d1000 r--p 00009000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
015d1000-015d2000 rw-p 0000a000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
02532000-0253b000 r-xp 00000000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
0253b000-0253c000 r--p 00008000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
0253c000-0253d000 rw-p 00009000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
0344d000-034be000 r-xp 00000000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
034be000-034c2000 r--p 00070000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
034c2000-034c3000 rw-p 00074000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
0376b000-037fe000 r-xp 00000000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
037fe000-037ff000 r--p 00092000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
037ff000-03816000 rw-p 00093000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
03e8e000-03f07000 r-xp 00000000 08:01 573        /lib/libgcrypt.so.11.5.2
03f07000-03f08000 r--p 00078000 08:01 573        /lib/libgcrypt.so.11.5.2
03f08000-03f0a000 rw-p 00079000 08:01 573        /lib/libgcrypt.so.11.5.2
03f4b000-03f9a000 r-xp 00000000 08:01 2429       /usr/lib/libXt.so.6.0.0
03f9a000-03f9b000 r--p 0004f000 08:01 2429       /usr/lib/libXt.so.6.0.0
03f9b000-03f9e000 rw-p 00050000 08:01 2429       /usr/lib/libXt.so.6.0.0
0443a000-0443c000 r-xp 00000000 08:01 524900     /usr/lib/gconv/UTF-32.so
0443c000-0443d000 r--p 00001000 08:01 524900     /usr/lib/gconv/UTF-32.so
0443d000-0443e000 rw-p 00002000 08:01 524900     /usr/lib/gconv/UTF-32.so
047c7000-047e3000 r-xp 00000000 08:01 3422       /usr/lib/libxcb.so.1.1.0
047e3000-047e4000 r--p 0001c000 08:01 3422       /usr/lib/libxcb.so.1.1.0
047e4000-047e5000 rw-p 0001d000 08:01 3422       /usr/lib/libxcb.so.1.1.0
04a40000-04a4e000 r-xp 00000000 08:01 2403       /usr/lib/libXext.so.6.4.0
04a4e000-04a4f000 r--p 0000d000 08:01 2403       /usr/lib/libXext.so.6.4.0
04a4f000-04a50000 rw-p 0000e000 08:01 2403       /usr/lib/libXext.so.6.4.0
04d94000-04d9a000 r-xp 00000000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
04d9a000-04d9b000 r--p 00005000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
04d9b000-04d9c000 rw-p 00006000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
056b4000-056b8000 r-xp 00000000 08:01 2401       /usr/lib/libXdmcp.so.6.0.0
056b8000-056b9000 rw-p 00003000 08:01 2401       /usr/lib/libXdmcp.so.6.0.0
05d97000-05ec1000 r-xp 00000000 08:01 2384       /usr/lib/libX11.so.6.2.0
05ec1000-05ec2000 ---p 0012a000 08:01 2384       /usr/lib/libX11.so.6.2.0
05ec2000-05ec3000 r--p 0012a000 08:01 2384       /usr/lib/libX11.so.6.2.0
05ec3000-05ec5000 rw-p 0012b000 08:01 2384       /usr/lib/libX11.so.6.2.0
05ec5000-05ec6000 rw-p 00000000 00:00 0 
063d4000-063db000 r-xp 00000000 08:01 2382       /usr/lib/libSM.so.6.0.0
063db000-063dc000 r--p 00006000 08:01 2382       /usr/lib/libSM.so.6.0.0
063dc000-063dd000 rw-p 00007000 08:01 2382       /usr/lib/libSM.so.6.0.0
06529000-065c4000 r-xp 00000000 08:01 20767      /usr/lib/libGL.so.195.22
065c4000-065de000 rwxp 0009a000 08:01 20767      /usr/lib/libGL.so.195.22
065de000-065ed000 rwxp 00000000 00:00 0 
06ac5000-06ada000 r-xp 00000000 08:01 2466       /usr/lib/libart_lgpl_2.so.2.3.20
06ada000-06adc000 rw-p 00014000 08:01 2466       /usr/lib/libart_lgpl_2.so.2.3.20
06c31000-06c48000 r-xp 00000000 08:01 2415       /usr/lib/libXmu.so.6.2.0
06c48000-06c49000 r--p 00016000 08:01 2415       /usr/lib/libXmu.so.6.2.0
06c49000-06c4a000 rw-p 00017000 08:01 2415       /usr/lib/libXmu.so.6.2.0
07e35000-07e37000 r-xp 00000000 08:01 2390       /usr/lib/libXau.so.6.0.0
07e37000-07e38000 r--p 00001000 08:01 2390       /usr/lib/libXau.so.6.0.0
07e38000-07e39000 rw-p 00002000 08:01 2390       /usr/lib/libXau.so.6.0.0
08048000-08071000 r-xp 00000000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08071000-08072000 r--p 00028000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08072000-0807e000 rw-p 00029000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08fe9000-09000000 r-xp 00000000 08:01 2353       /usr/lib/libICE.so.6.3.0
09000000-09001000 r--p 00016000 08:01 2353       /usr/lib/libICE.so.6.3.0
09001000-09002000 rw-p 00017000 08:01 2353       /usr/lib/libICE.so.6.3.0
09002000-09004000 rw-p 00000000 00:00 0 
092ca000-09690000 rw-p 00000000 00:00 0          [heap]
b5d00000-b5d21000 rw-p 00000000 00:00 0 
b5d21000-b5e00000 ---p 00000000 00:00 0 
b5ed7000-b5f11000 rw-p 00000000 00:00 0 
b5f39000-b5f3f000 rw-p 00000000 00:00 0 
b5fb9000-b7493000 r-xp 00000000 08:01 9661       /usr/lib/libGLcore.so.195.22
b7493000-b74e4000 rwxp 014da000 08:01 9661       /usr/lib/libGLcore.so.195.22
b74e4000-b74f3000 rwxp 00000000 00:00 0 
b753b000-b755e000 rw-p 00000000 00:00 0 
b7581000-b75c0000 r--p 00000000 08:01 1048731    /usr/lib/locale/en_US.utf8/LC_CTYPE
b75c0000-b75c1000 r--p 00000000 08:01 1048736    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b75c1000-b75c2000 r--p 00000000 08:01 1180560    /usr/lib/locale/en_US.utf8/LC_TIME
b75c2000-b76af000 r--p 00000000 08:01 1048730    /usr/lib/locale/en_US.utf8/LC_COLLATE
b76af000-b77bd000 r--p 00000000 08:01 786590     /usr/lib/locale/locale-archive
b77bd000-b77c6000 rw-p 00000000 00:00 0 
b77f0000-b77ff000 rw-p 00000000 00:00 0 
b77ff000-b7800000 r--p 00000000 08:01 1180561    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7800000-b7801000 r--p 00000000 08:01 1573349    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7801000-b7802000 r--p 00000000 08:01 1311163    /usr/lib/locale/en_US.utf8/LC_PAPER
b7802000-b7803000 r--p 00000000 08:01 1048658    /usr/lib/locale/en_US.utf8/LC_NAME
b7803000-b7804000 r--p 00000000 08:01 1180562    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7804000-b7805000 r--p 00000000 08:01 1180563    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7805000-b7806000 r--p 00000000 08:01 1311137    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7806000-b780d000 r--s 00000000 08:01 524904     /usr/lib/gconv/gconv-modules.cache
b780d000-b780e000 r--p 00000000 08:01 1180564    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b780e000-b7810000 rw-p 00000000 00:00 0 
bfa78000-bfa92000 rwxp 00000000 00:00 0          [stack]
*** glibc detected *** /usr/bin/Terminal: free(): invalid pointer: 0x07625e58 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xbd4ff1]
/lib/tls/i686/cmov/libc.so.6[0xbd66f2]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xbd979d]
/usr/lib/tls/libnvidia-tls.so.1[0x5cab00]
/usr/lib/libgnustep-gui.so.0.16[0x1e6300]
/usr/lib/libgnustep-gui.so.0.16[0x1dd3e0]
/usr/lib/libgnustep-gui.so.0.16[0x26e008]
/usr/lib/libgnustep-gui.so.0.16[0x26b144]
/usr/lib/libgnustep-gui.so.0.16[0x2693f1]
/usr/lib/libgnustep-gui.so.0.16[0x269639]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x5dbb6d6]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x5dbbb71]
/usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/./libgnustep-art-016[0x5dbc402]
/usr/lib/libgnustep-gui.so.0.16[0x347144]
/usr/lib/libgnustep-gui.so.0.16[0x347b9f]
/usr/lib/libgnustep-gui.so.0.16[0x1ce6a9]
/usr/lib/libgnustep-gui.so.0.16[0x1c6b2c]
/usr/lib/libgnustep-gui.so.0.16[0x1c8836]
/usr/bin/Terminal(main+0x130)[0x804d330]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb80b56]
/usr/bin/Terminal[0x804aa41]
======= Memory map: ========
00110000-00449000 r-xp 00000000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
00449000-0044a000 r--p 00339000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
0044a000-00526000 rw-p 0033a000 08:01 102325     /usr/lib/libgnustep-gui.so.0.16.0
00526000-00527000 rw-p 00000000 00:00 0 
00527000-0053c000 r-xp 00000000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
0053c000-0053d000 r--p 00014000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
0053d000-0053e000 rw-p 00015000 08:01 3014785    /lib/tls/i686/cmov/libpthread-2.10.1.so
0053e000-00540000 rw-p 00000000 00:00 0 
00540000-0055c000 r-xp 00000000 08:01 571        /lib/libgcc_s.so.1
0055c000-0055d000 r--p 0001b000 08:01 571        /lib/libgcc_s.so.1
0055d000-0055e000 rw-p 0001c000 08:01 571        /lib/libgcc_s.so.1
0055e000-00584000 r-xp 00000000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
00584000-00585000 ---p 00026000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
00585000-00586000 r--p 00026000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
00586000-00588000 rw-p 00027000 08:01 2478       /usr/lib/libaudiofile.so.0.0.2
00588000-0058f000 r-xp 00000000 08:01 2755       /usr/lib/libgif.so.4.1.6
0058f000-00590000 r--p 00006000 08:01 2755       /usr/lib/libgif.so.4.1.6
00590000-00591000 rw-p 00007000 08:01 2755       /usr/lib/libgif.so.4.1.6
00591000-005b7000 r-xp 00000000 08:01 32038      /usr/lib/libpng12.so.0.39.0
005b7000-005b8000 r--p 00025000 08:01 32038      /usr/lib/libpng12.so.0.39.0
005b8000-005b9000 rw-p 00026000 08:01 32038      /usr/lib/libpng12.so.0.39.0
005b9000-005c0000 r-xp 00000000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
005c0000-005c1000 r--p 00006000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
005c1000-005c2000 rw-p 00007000 08:01 102112     /usr/lib/libdns_sd.so.1.0.0
005c2000-005c7000 r-xp 00000000 08:01 2686       /usr/lib/libffi.so.5.0.8
005c7000-005c8000 ---p 00005000 08:01 2686       /usr/lib/libffi.so.5.0.8
005c8000-005c9000 r--p 00005000 08:01 2686       /usr/lib/libffi.so.5.0.8
005c9000-005ca000 rw-p 00006000 08:01 2686       /usr/lib/libffi.so.5.0.8
005ca000-005cb000 r-xp 00000000 08:01 1216806    /usr/lib/tls/libnvidia-tls.so.195.22
005cb000-005cc000 rw-p 00000000 08:01 1216806    /usr/lib/tls/libnvidia-tls.so.195.22
005cc000-005ce000 r-xp 00000000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
005ce000-005cf000 r--p 00001000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
005cf000-005d0000 rw-p 00002000 08:01 3014793    /lib/tls/i686/cmov/libutil-2.10.1.so
005d0000-00952000 r-xp 00000000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
00952000-00953000 r--p 00382000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
00953000-009d8000 rw-p 00383000 08:01 102139     /usr/lib/libgnustep-base.so.1.19.0
009d8000-009d9000 rw-p 00000000 00:00 0 
009d9000-009ed000 r-xp 00000000 08:01 673        /lib/libz.so.1.2.3.3
009ed000-009ee000 r--p 00013000 08:01 673        /lib/libz.so.1.2.3.3
009ee000-009ef000 rw-p 00014000 08:01 673        /lib/libz.so.1.2.3.3
009ef000-00a0f000 r-xp 00000000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
00a0f000-00a10000 r--p 0001f000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
00a10000-00a11000 rw-p 00020000 08:01 32110      /usr/lib/libjpeg.so.62.0.0
00a11000-00a46000 r-xp 00000000 08:01 3430       /usr/lib/libxslt.so.1.1.24
00a46000-00a47000 r--p 00034000 08:01 3430       /usr/lib/libxslt.so.1.1.24
00a47000-00a48000 rw-p 00035000 08:01 3430       /usr/lib/libxslt.so.1.1.24
00a48000-00a4a000 r-xp 00000000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00a4a000-00a4b000 r--p 00001000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00a4b000-00a4c000 rw-p 00002000 08:01 3014765    /lib/tls/i686/cmov/libdl-2.10.1.so
00a4c000-00a4f000 r-xp 00000000 08:01 577        /lib/libgpg-error.so.0.4.0
00a4f000-00a50000 r--p 00002000 08:01 577        /lib/libgpg-error.so.0.4.0
00a50000-00a51000 rw-p 00003000 08:01 577        /lib/libgpg-error.so.0.4.0
00a54000-00a6a000 r-xp 00000000 08:01 102127     /usr/lib/libobjc.so.2.0.0
00a6a000-00a6b000 r--p 00015000 08:01 102127     /usr/lib/libobjc.so.2.0.0
00a6b000-00a6d000 rw-p 00016000 08:01 102127     /usr/lib/libobjc.so.2.0.0
00a6d000-00a6e000 rw-p 00000000 00:00 0 
00a6e000-00b0c000 r-xp 00000000 08:01 2470       /usr/lib/libaspell.so.15.1.4
00b0c000-00b0f000 r--p 0009e000 08:01 2470       /usr/lib/libaspell.so.15.1.4
00b0f000-00b10000 rw-p 000a1000 08:01 2470       /usr/lib/libaspell.so.15.1.4
00b10000-00b14000 rw-p 00000000 00:00 0 
00b14000-00b27000 r-xp 00000000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
00b27000-00b28000 r--p 00012000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
00b28000-00b29000 rw-p 00013000 08:01 3014770    /lib/tls/i686/cmov/libnsl-2.10.1.so
00b29000-00b2b000 rw-p 00000000 00:00 0 
00b2b000-00b2d000 r-xp 00000000 08:01 524899     /usr/lib/gconv/UTF-16.so
00b2d000-00b2e000 r--p 00001000 08:01 524899     /usr/lib/gconv/UTF-16.so
00b2e000-00b2f000 rw-p 00002000 08:01 524899     /usr/lib/gconv/UTF-16.so
00b32000-00b56000 r-xp 00000000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
00b56000-00b57000 r--p 00023000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
00b57000-00b58000 rw-p 00024000 08:01 3014767    /lib/tls/i686/cmov/libm-2.10.1.so
00b58000-00b66000 r-xp 00000000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
00b66000-00b67000 ---p 0000e000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
00b67000-00b68000 r--p 0000e000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
00b68000-00b69000 rw-p 0000f000 08:01 13243      /usr/lib/libavahi-client.so.3.2.5
00b69000-00b6a000 r-xp 00000000 00:00 0          [vdso]
00b6a000-00ca8000 r-xp 00000000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00ca8000-00caa000 r--p 0013e000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00caa000-00cab000 rw-p 00140000 08:01 3014759    /lib/tls/i686/cmov/libc-2.10.1.so
00cab000-00cae000 rw-p 00000000 00:00 0 
00cae000-00ce5000 r-xp 00000000 08:01 557        /lib/libdbus-1.so.3.4.0
00ce5000-00ce6000 r--p 00036000 08:01 557        /lib/libdbus-1.so.3.4.0
00ce6000-00ce7000 rw-p 00037000 08:01 557        /lib/libdbus-1.so.3.4.0
00ce7000-00cee000 r-xp 00000000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
00cee000-00cef000 r--p 00006000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
00cef000-00cf0000 rw-p 00007000 08:01 3014789    /lib/tls/i686/cmov/librt-2.10.1.so
00cf0000-00cfa000 r-xp 00000000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00cfa000-00cfb000 r--p 00009000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00cfb000-00cfc000 rw-p 0000a000 08:01 13177      /usr/lib/libavahi-common.so.3.5.1
00cff000-00d1a000 r-xp 00000000 08:01 521        /lib/ld-2.10.1.so
00d1a000-00d1b000 r--p 0001a000 08:01 521        /lib/ld-2.10.1.so
00d1b000-00d1c000 rw-p 0001b000 08:01 521        /lib/ld-2.10.1.so
00d1c000-00dbf000 r-xp 00000000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00dbf000-00dc3000 r--p 000a2000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00dc3000-00dc4000 rw-p 000a6000 08:01 2829       /usr/lib/libgnutls.so.26.14.10
00dc4000-00ee6000 r-xp 00000000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00ee6000-00ee7000 ---p 00122000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00ee7000-00eeb000 r--p 00122000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00eeb000-00eec000 rw-p 00126000 08:01 3428       /usr/lib/libxml2.so.2.7.5
00eec000-00eed000 rw-p 00000000 00:00 0 
00eed000-00efd000 r-xp 00000000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00efd000-00efe000 r--p 0000f000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00efe000-00eff000 rw-p 00010000 08:01 3332       /usr/lib/libtasn1.so.3.1.5
00eff000-00f01000 r-xp 00000000 08:01 524900     /usr/lib/gconv/UTF-32.so
00f01000-00f02000 r--p 00001000 08:01 524900     /usr/lib/gconv/UTF-32.so
00f02000-00f03000 rw-p 00002000 08:01 524900     /usr/lib/gconv/UTF-32.so
00f03000-00f09000 r-xp 00000000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
00f09000-00f0a000 r--p 00005000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
00f0a000-00f0b000 rw-p 00006000 08:01 3014772    /lib/tls/i686/cmov/libnss_compat-2.10.1.so
00f0b000-00f12000 r-xp 00000000 08:01 2382       /usr/lib/libSM.so.6.0.0
00f12000-00f13000 r--p 00006000 08:01 2382       /usr/lib/libSM.so.6.0.0
00f13000-00f14000 rw-p 00007000 08:01 2382       /usr/lib/libSM.so.6.0.0
00f14000-00f71000 r-xp 00000000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00f71000-00f73000 r--p 0005c000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00f73000-00f74000 rw-p 0005e000 08:01 1216438    /usr/lib/libtiff.so.4.3.1
00f74000-0105a000 r-xp 00000000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
0105a000-0105e000 r--p 000e6000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
0105e000-0105f000 rw-p 000ea000 08:01 3325       /usr/lib/libstdc++.so.6.0.13
0105f000-01066000 rw-p 00000000 00:00 0 
01ae1000-01aea000 r-xp 00000000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
01aea000-01aeb000 r--p 00008000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
01aeb000-01aec000 rw-p 00009000 08:01 3014780    /lib/tls/i686/cmov/libnss_nis-2.10.1.so
02893000-02895000 r-xp 00000000 08:01 2390       /usr/lib/libXau.so.6.0.0
02895000-02896000 r--p 00001000 08:01 2390       /usr/lib/libXau.so.6.0.0
02896000-02897000 rw-p 00002000 08:01 2390       /usr/lib/libXau.so.6.0.0
02cd6000-02cf2000 r-xp 00000000 08:01 3422       /usr/lib/libxcb.so.1.1.0
02cf2000-02cf3000 r--p 0001c000 08:01 3422       /usr/lib/libxcb.so.1.1.0
02cf3000-02cf4000 rw-p 0001d000 08:01 3422       /usr/lib/libxcb.so.1.1.0
02f44000-02f5b000 r-xp 00000000 08:01 2353       /usr/lib/libICE.so.6.3.0
02f5b000-02f5c000 r--p 00016000 08:01 2353       /usr/lib/libICE.so.6.3.0
02f5c000-02f5d000 rw-p 00017000 08:01 2353       /usr/lib/libICE.so.6.3.0
02f5d000-02f5f000 rw-p 00000000 00:00 0 
0357d000-03592000 r-xp 00000000 08:01 2466       /usr/lib/libart_lgpl_2.so.2.3.20
03592000-03594000 rw-p 00014000 08:01 2466       /usr/lib/libart_lgpl_2.so.2.3.20
03cc6000-03cdd000 r-xp 00000000 08:01 2415       /usr/lib/libXmu.so.6.2.0
03cdd000-03cde000 r--p 00016000 08:01 2415       /usr/lib/libXmu.so.6.2.0
03cde000-03cdf000 rw-p 00017000 08:01 2415       /usr/lib/libXmu.so.6.2.0
049a6000-04ad0000 r-xp 00000000 08:01 2384       /usr/lib/libX11.so.6.2.0
04ad0000-04ad1000 ---p 0012a000 08:01 2384       /usr/lib/libX11.so.6.2.0
04ad1000-04ad2000 r--p 0012a000 08:01 2384       /usr/lib/libX11.so.6.2.0
04ad2000-04ad4000 rw-p 0012b000 08:01 2384       /usr/lib/libX11.so.6.2.0
04ad4000-04ad5000 rw-p 00000000 00:00 0 
05d80000-05e13000 r-xp 00000000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
05e13000-05e14000 r--p 00092000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
05e14000-05e2b000 rw-p 00093000 08:01 102402     /usr/lib/GNUstep/Bundles/libgnustep-art-016.bundle/libgnustep-art-016
05e2b000-07305000 r-xp 00000000 08:01 9661       /usr/lib/libGLcore.so.195.22
07305000-07356000 rwxp 014da000 08:01 9661       /usr/lib/libGLcore.so.195.22
07356000-07365000 rwxp 00000000 00:00 0 
07571000-0760c000 r-xp 00000000 08:01 20767      /usr/lib/libGL.so.195.22
0760c000-07626000 rwxp 0009a000 08:01 20767      /usr/lib/libGL.so.195.22
07626000-07635000 rwxp 00000000 00:00 0 
07b08000-07b16000 r-xp 00000000 08:01 2403       /usr/lib/libXext.so.6.4.0
07b16000-07b17000 r--p 0000d000 08:01 2403       /usr/lib/libXext.so.6.4.0
07b17000-07b18000 rw-p 0000e000 08:01 2403       /usr/lib/libXext.so.6.4.0
07f2c000-07f9d000 r-xp 00000000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
07f9d000-07fa1000 r--p 00070000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
07fa1000-07fa2000 rw-p 00074000 08:01 32016      /usr/lib/libfreetype.so.6.3.22
08048000-08071000 r-xp 00000000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08071000-08072000 r--p 00028000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08072000-0807e000 rw-p 00029000 08:01 137025     /usr/lib/GNUstep/Applications/Terminal.app/Terminal
08166000-0816a000 r-xp 00000000 08:01 2401       /usr/lib/libXdmcp.so.6.0.0
0816a000-0816b000 rw-p 00003000 08:01 2401       /usr/lib/libXdmcp.so.6.0.0
08636000-08640000 r-xp 00000000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
08640000-08641000 r--p 00009000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
08641000-08642000 rw-p 0000a000 08:01 3014776    /lib/tls/i686/cmov/libnss_files-2.10.1.so
08920000-08999000 r-xp 00000000 08:01 573        /lib/libgcrypt.so.11.5.2
08999000-0899a000 r--p 00078000 08:01 573        /lib/libgcrypt.so.11.5.2
0899a000-0899c000 rw-p 00079000 08:01 573        /lib/libgcrypt.so.11.5.2
0907c000-090cb000 r-xp 00000000 08:01 2429       /usr/lib/libXt.so.6.0.0
090cb000-090cc000 r--p 0004f000 08:01 2429       /usr/lib/libXt.so.6.0.0
090cc000-090cf000 rw-p 00050000 08:01 2429       /usr/lib/libXt.so.6.0.0
093f7000-093fa000 r-xp 00000000 08:01 666        /lib/libuuid.so.1.3.0
093fa000-093fb000 r--p 00002000 08:01 666        /lib/libuuid.so.1.3.0
093fb000-093fc000 rw-p 00003000 08:01 666        /lib/libuuid.so.1.3.0
0948f000-09855000 rw-p 00000000 00:00 0          [heap]
b7300000-b7321000 rw-p 00000000 00:00 0 
b7321000-b7400000 ---p 00000000 00:00 0 
b7473000-b74ad000 rw-p 00000000 00:00 0 
b74d5000-b74db000 rw-p 00000000 00:00 0 
b754f000-b7578000 rw-p 00000000 00:00 0 
b759b000-b75da000 r--p 00000000 08:01 1048731    /usr/lib/locale/en_US.utf8/LC_CTYPE
b75da000-b75db000 r--p 00000000 08:01 1048736    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b75db000-b75dc000 r--p 00000000 08:01 1180560    /usr/lib/locale/en_US.utf8/LC_TIME
b75dc000-b76c9000 r--p 00000000 08:01 1048730    /usr/lib/locale/en_US.utf8/LC_COLLATE
b76c9000-b77d7000 r--p 00000000 08:01 786590     /usr/lib/locale/locale-archive
b77d7000-b77e0000 rw-p 00000000 00:00 0 
b7810000-b7819000 rw-p 00000000 00:00 0 
b7819000-b781a000 r--p 00000000 08:01 1180561    /usr/lib/locale/en_US.utf8/LC_MONETARY
b781a000-b781b000 r--p 00000000 08:01 1573349    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b781b000-b781c000 r--p 00000000 08:01 1311163    /usr/lib/locale/en_US.utf8/LC_PAPER
b781c000-b781d000 r--p 00000000 08:01 1048658    /usr/lib/locale/en_US.utf8/LC_NAME
b781d000-b781e000 r--p 00000000 08:01 1180562    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b781e000-b781f000 r--p 00000000 08:01 1180563    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b781f000-b7820000 r--p 00000000 08:01 1311137    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7820000-b7827000 r--s 00000000 08:01 524904     /usr/lib/gconv/gconv-modules.cache
b7827000-b7828000 r--p 00000000 08:01 1180564    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7828000-b782a000 rw-p 00000000 00:00 0 
bf922000-bf93b000 rwxp 00000000 00:00 0          [stack]
bf93b000-bf93d000 rw-p 00000000 00:00 0 

(gcursor:12974): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(gcursor:12974): libglade-WARNING **: could not find signal handler 'entry_selected'.

(gcursor:12974): libglade-WARNING **: could not find signal handler 'open_theme_dir'.

(gcursor:12974): libglade-WARNING **: could not find signal handler 'size_changed'.

(gcursor:12974): libglade-WARNING **: could not find signal handler 'extract_theme'.
** Message: xfsm-shutdown-helper.c:268: Using HAL to shutdown/reboot the computer.

(polkit-gnome-authentication-agent-1:5567): polkit-gnome-1-WARNING **: Error enumerating temporary authorizations: Remote Exception invoking org.freedesktop.PolicyKit1.Authority.EnumerateTemporaryAuthorizations() on /org/freedesktop/PolicyKit1/Authority at name org.freedesktop.PolicyKit1: org.freedesktop.PolicyKit1.Error.Failed: Cannot determine session the caller is in
xfsettingsd: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-places-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-menu-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
polkit-gnome-authentication-agent-1: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-mixer-plugin: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
wicd-client.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
maximus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
parcellite: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-power-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
xfce4-volstatus-icon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-volume-control-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
bluetooth-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"

caught XIO error:
      after 985 requests (984 known processed) with 3 events remaining.

The application 'xfce4-panel' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
30/11/2009 05:20:17 PM deleted 80 tile_row polling images.
```

**My xorg.conf file**
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Sun Nov 22 18:17:43 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    FontPath        "unix/:7100"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "yes"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "NEC MultiSync 75"
    HorizSync       31.0 - 70.0
    VertRefresh     55.0 - 120.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1280x1024 +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



```

 Please help me!!! I do not want to reinstall a third time

---

