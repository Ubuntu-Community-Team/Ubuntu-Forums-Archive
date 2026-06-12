---
title: "Have someone got this problem"
date: 2010-04-02
forum: General Help
---

### Post by gretarsson on 2010-04-02
Hi I have ubuntu 9.10 with 2 users but if I log in I always got lot of music files on me desktop bottom (see photo) the other user dont have this but I am not sore what is doing this, any idea? here is my running script 
jon@jon:~$ ps -U jon
  PID TTY          TIME CMD
 2206 ?        00:00:00 gnome-keyring-d
 2221 ?        00:00:00 gnome-session
 2263 ?        00:00:00 ssh-agent
 2266 ?        00:00:00 dbus-launch
 2267 ?        00:00:01 dbus-daemon
 2271 ?        00:27:21 pulseaudio
 2274 ?        00:00:00 gconf-helper
 2276 ?        00:00:39 gconfd-2
 2285 ?        00:00:34 gnome-settings-
 2290 ?        00:00:00 seahorse-daemon
 2293 ?        00:00:00 gvfsd
 2299 ?        00:00:10 notify-osd
 2308 ?        00:00:00 gvfs-fuse-daemo
 2317 ?        00:16:32 compiz.real
 2320 ?        00:02:41 gnome-panel
 2321 ?        00:00:00 sh
 2322 ?        00:00:34 gtk-window-deco
 2324 ?        00:04:40 nautilus
 2326 ?        00:00:00 bonobo-activati
 2328 ?        00:00:00 evolution-alarm
 2333 ?        00:00:01 nm-applet
 2344 ?        00:00:00 polkit-gnome-au
 2348 ?        00:00:00 gdu-notificatio
 2349 ?        00:00:00 gnome-volume-co
 2354 ?        00:00:10 update-notifier
 2357 ?        00:00:02 gnome-power-man
 2363 ?        00:00:10 gnome-screensav
 2367 ?        00:00:00 evolution-data-
 2375 ?        00:00:00 gvfsd-trash
 2397 ?        00:00:00 gvfs-gdu-volume
 2401 ?        00:00:00 gvfs-gphoto2-vo
 2408 ?        00:00:00 gvfsd-burn
 2421 ?        00:00:00 trashapplet
 2426 ?        00:00:00 indicator-apple
 2431 ?        00:00:00 indicator-apple
 2434 ?        00:00:00 indicator-statu
 2436 ?        00:00:00 indicator-users
 2438 ?        00:00:00 indicator-sessi
 2440 ?        00:00:00 indicator-messa
 2534 ?        00:00:00 gvfsd-metadata
 4696 ?        01:31:57 firefox
 8683 ?        00:00:00 evolution-excha
13558 ?        00:05:02 transmission
15378 ?        00:00:00 gvfsd-archive
15574 ?        00:08:15 npviewer.bin
15952 ?        00:00:00 gnome-terminal
15953 ?        00:00:00 gnome-pty-helpe
15954 pts/0    00:00:00 bash
16020 pts/0    00:00:00 ps
jon@jon:~$

---

### Post by everytimeref on 2010-04-02
Have you looked in the system menu: preferences/ startup applications to see if there are any Apps launching at startup that shouldn't be?

If you right click on them and select "remove from panel" for all of them, do they reappear the next time you restart?

---

