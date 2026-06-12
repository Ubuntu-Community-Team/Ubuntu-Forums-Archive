---
title: "No desktop,icons, no reaction :/"
date: 2012-01-22
forum: General Help
---

### Post by mazi1313 on 2012-01-22
I have problem that suddenly my desktop, icons gone. In places(desktop) everything is fine but on desktop i can't do anything(RMB). When i want to change my wallpaper it displays "can not start the settings manager - "gnome-settings-daemon".
 Without the GNOME settings manager running some settings may not enter into life. This may indicate a problem with Bonobo, or from running other settings manager (eg KDE), colliding manager GNOME." I don't know what to do, I tried to log in again(Ctrl+shift+backspace) but id didn't work :/

---

### Post by yetiman64 on 2012-01-22
What version number of Ubuntu are you running ?

---

### Post by mazi1313 on 2012-01-22
Ubutu 8.04(i downgraded it long time ago) XFCE & GNOME. I think 8.04 is more stable :) I have very slow pc(768mb RAM) :/
And in my home folder i have sth like: .xsession-errors  
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=pl_PL.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/startxfce4: X server already running on display :0
xrdb:  "Xft.hinting" on line 9 overrides entry on line 6
xrdb:  "Xft.hintstyle" on line 10 overrides entry on line 7
Agent pid 5913
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-MEkvUJ5912/agent.5912


Tracker version 0.6.6 Copyright (c) 2005-2007 by Jamie McCracken (jamiemcc@gnome.org)

This program is free software and comes without any warranty.
It is licensed under version 2 or later of the General Public License which can be viewed at http://www.gnu.org/licenses/gpl.txt

Initialising tracker...
Could not set idle IO priority...attempting best effort 7 priority
Connection failure: Connection refused
A panel is already running.

** (update-notifier:5945): WARNING **: already running?

starting HAL detection for ac adaptors...A panel is already running.
none found
Throttle level is 0

(gnome-panel:5927): Wnck-WARNING **: Property _NET_WM_NAME contained invalid UTF-8


(gnome-panel:5927): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -9 and height 24

(rhythmbox:5936): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
  PID TTY          TIME CMD
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6260): WARNING **: Unable to add monitor: Nieobs&#322;ugiwane
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" zwróci&#322; b&#322;&#261;d 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" zwróci&#322; b&#322;&#261;d 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" zwróci&#322; b&#322;&#261;d 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Error: /undefined in d
Operand stack:
   CP   false
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1909   1   3   %oparray_pop   1908   1   3   %oparray_pop   1892   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1153/1684(ro)(G)--   --dict:0/20(G)--   --dict:92/200(L)--
Current allocation mode is local
Current file position is 302
GPL Ghostscript 8.61: Unrecoverable error, exit code 1

** (evince-thumbnailer:6399): WARNING **: Interpreter failed.
Warning: you will not be able to convert protected fonts.
If you need to convert a protected font, please
restart the program and specify the -dWRITESYSTEMDICT switch.

** (evince-thumbnailer:6403): WARNING **: Interpreter failed.

** (evince-thumbnailer:6407): WARNING **: Interpreter failed.
Error: /undefined in .runlibfile
Operand stack:
   (Fontmap.GS)
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1909   1   3   %oparray_pop   1908   1   3   %oparray_pop   1892   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1153/1684(ro)(G)--   --dict:0/20(G)--   --dict:92/200(L)--
Current allocation mode is local
Current file position is 109
GPL Ghostscript 8.61: Unrecoverable error, exit code 1

** (evince-thumbnailer:6417): WARNING **: Interpreter failed.
Error: /undefined in .forceput
Operand stack:
   --dict:1153/1684(ro)(G)--   .nativefontmapbuilt   false
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1909   1   3   %oparray_pop   1908   1   3   %oparray_pop   1892   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1153/1684(ro)(G)--   --dict:0/20(G)--   --dict:105/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 13579
GPL Ghostscript 8.61: Unrecoverable error, exit code 1

** (evince-thumbnailer:6422): WARNING **: Interpreter failed.
could not load face 'file:///usr/share/a2ps/fonts/pcfont.pfa': broken file
Error: /undefined in .forceput
Operand stack:
   false   true   --dict:1120/1684(ro)(G)--   .pdforigfontcache_l   --dict:0/20(L)--
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1909   1   3   %oparray_pop   1908   1   3   %oparray_pop   1892   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1120/1684(ro)(G)--   --dict:0/20(G)--   --dict:92/200(L)--   --dict:107/127(ro)(G)--   --dict:275/300(G)--
Current allocation mode is local
Current file position is 21063
GPL Ghostscript 8.61: Unrecoverable error, exit code 1

** (evince-thumbnailer:6427): WARNING **: Interpreter failed.

** (evince-thumbnailer:6431): WARNING **: Interpreter failed.
Error: /stackunderflow in --pop--
Operand stack:

Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1909   1   3   %oparray_pop   1908   1   3   %oparray_pop   1892   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   227   1   255   --nostringval--   %for_pos_int_continue
Dictionary stack:
   --dict:1153/1684(ro)(G)--   --dict:0/20(G)--   --dict:93/200(L)--   --dict:26/100(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 5223
GPL Ghostscript 8.61: Unrecoverable error, exit code 1

** (evince-thumbnailer:6436): WARNING **: Interpreter failed.
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" zwróci&#322; b&#322;&#261;d 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

seahorse nautilus module shutdown

--- Hash table keys for warning below:
--> x-nautilus-search://0/
--> file:///usr/share
--> file:///home/michal13
--> file:///
--> x-nautilus-search://1/

(nautilus:6260): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 5 elements at quit time (keys above)

(nautilus:6260): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 5 elements at quit time
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7226): WARNING **: Unable to add monitor: Nieobs&#322;ugiwane
Nautilus-Share-Message: Called "net usershare info" but it failed: "net usershare" zwróci&#322; b&#322;&#261;d 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```
& and i have Polish version of ubuntu :)

---

### Post by Cheesemill on 2012-01-22
This isn't a solution but do you know that 8.04 isn't supported anymore on a desktop machine (support ran out almost a year ago).

This means that you wont get any more bug or security fixes for any of your software, it also means that there wont be many people running 8.04 anymore to help solve your issue.

---

