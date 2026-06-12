---
title: "All music players no longer have sound"
date: 2010-04-11
forum: General Help
---

### Post by entikryst on 2010-04-11
I switched to Thunar as my file manager and now banshee and rhythmbox play without sound.  I had a similar problem but was fixed by adding pulseaudio & to my fluxbox start up file.

entikryst@entikryst-desktop:~$ rhythmbox

** (rhythmbox:2692): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2692): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2692): Rhythmbox-WARNING **: Unable to grab media player keys: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

(<unknown>:2708): GLib-WARNING **: g_set_prgname() called multiple times

---

### Post by entikryst on 2010-04-12
Solved my own problem I just took pulseaudio out of my fluxbox startup file.  I guess if it randomly happens I will put it back in.

---

