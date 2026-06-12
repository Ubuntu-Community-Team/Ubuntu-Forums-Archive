---
title: "nautilus won't run"
date: 2011-02-16
forum: General Help
---

### Post by Aaron.A on 2011-02-16
hey
not sure what i did or if someone did it to me but nautilus will not run at log in or via menu launcher. i tried gksu nautilus with no luck. heres what i get
```
(nautilus:1875): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
call g_type_init()

```the last thing i did was chown /usr/share/applications so i could modify the launcher icons from nautilus. the last thing i did before that was download the packages required to build docky and then built and installed the latest docky. 
not sure if any of that helps.. 

please help! =D

---

### Post by sikander3786 on 2011-02-16
Changing permissions or ownership on any of the system directories/files is not recommended.

Please post the output of this command.

```
ls -l /usr/share/applications
```

---

### Post by Aaron.A on 2011-02-16
```

total 676
-rw-r--r-- 1 root root   396 2010-09-20 12:23 alacarte.desktop
-rw-r--r-- 1 root root   283 2010-12-03 17:51 apport-gtk-mime.desktop
-rw-r--r-- 1 root root   256 2010-06-13 06:38 arista.desktop
-rw-r--r-- 1 root root   522 2010-10-04 13:34 at-properties.desktop
-rw-r--r-- 1 root root   604 2010-09-22 00:27 audacity.desktop
-rw-r--r-- 1 root root   403 2010-08-05 08:49 baobab.desktop
-rw-r--r-- 1 root root   489 2010-10-01 05:17 bluetooth-properties.desktop
-rw-r--r-- 1 root root   713 2011-01-07 04:46 brasero.desktop
-rw-r--r-- 1 root root   530 2011-01-07 04:46 brasero-nautilus.desktop
-rw-r--r-- 1 root root   258 2010-09-15 20:49 byobu.desktop
-rw-r--r-- 1 root root  3062 2009-03-10 06:00 ccsm.desktop
-rw-r--r-- 1 root root   269 2010-09-16 00:38 checkbox-gtk.desktop
-rw-r--r-- 1 root root   396 2010-10-22 04:04 compiz.desktop
-rw-r--r-- 1 root root   333 2011-01-25 04:52 computer-janitor-gtk.desktop
-rw-r--r-- 1 root root   503 2010-10-04 13:34 default-applications.desktop
lrwxrwxrwx 1 root root    24 2011-02-12 08:27 defaults.list -> /etc/gnome/defaults.list
-rw-r--r-- 1 root root 36379 2011-02-15 07:31 desktop.en_US.utf8.cache
-rw-r--r-- 1 root root   465 2010-10-04 13:34 display-properties.desktop
-rw-r--r-- 1 root root   143 2010-10-02 14:08 docky.desktop
-rw-r--r-- 1 root root   560 2010-09-28 09:39 emerald-theme-manager.desktop
-rw-r--r-- 1 root root   450 2011-01-25 05:13 empathy-accounts.desktop
-rw-r--r-- 1 root root   468 2011-01-25 05:13 empathy.desktop
-rw-r--r-- 1 root root   747 2010-09-27 19:39 eog.desktop
-rw-r--r-- 1 root root   843 2011-01-03 15:31 evince.desktop
-rw-r--r-- 1 root root   465 2011-01-07 05:01 evolution-2.2.desktop
-rw-r--r-- 1 root root   888 2011-01-07 04:59 evolution.desktop
-rw-r--r-- 1 root root   451 2011-01-07 05:01 evolution-mail.desktop
-rw-r--r-- 1 root root   272 2011-01-07 04:59 evolution-settings.desktop
-rw-r--r-- 1 root root  1567 2010-09-27 18:51 file-roller.desktop
-rw-r--r-- 1 root root   489 2011-02-15 08:16 firefox.desktop
-rw-r--r-- 1 root root   427 2010-09-06 03:27 gbrainy.desktop
-rw-r--r-- 1 root root   470 2010-10-20 12:15 gcalctool.desktop
-rw-r--r-- 1 root root   404 2010-09-27 14:21 gconf-editor.desktop
-rw-r--r-- 1 root root   316 2010-09-13 09:48 gdmsetup.desktop
-rw-r--r-- 1 root root   520 2010-08-23 22:42 gedit.desktop
-rw-r--r-- 1 root root   338 2010-09-15 22:22 gksu.desktop
-rw-r--r-- 1 root root   270 2010-09-27 13:54 gmenu-simple-editor.desktop
-rw-r--r-- 1 root root   417 2010-09-27 12:46 gnome-about.desktop
-rw-r--r-- 1 root root   423 2010-10-04 13:34 gnome-about-me.desktop
-rw-r--r-- 1 root root   454 2010-10-04 13:34 gnome-appearance-properties.desktop
-rw-r--r-- 1 root root   436 2010-10-04 13:34 gnomecc.desktop
-rw-r--r-- 1 root root   485 2010-08-05 08:50 gnome-dictionary.desktop
-rw-r--r-- 1 root root  6548 2010-10-01 07:14 gnome-do.desktop
-rw-r--r-- 1 root root   483 2010-10-04 13:34 gnome-font-viewer.desktop
-rw-r--r-- 1 root root   382 2010-08-17 06:06 gnome-nettool.desktop
-rw-r--r-- 1 root root   468 2010-10-04 13:34 gnome-network-properties.desktop
-rw-r--r-- 1 root root   568 2010-08-27 06:15 gnome-panel.desktop
-rw-r--r-- 1 root root   529 2010-09-27 17:15 gnome-power-preferences.desktop
-rw-r--r-- 1 root root   414 2010-06-07 00:18 gnome-screensaver-preferences.desktop
-rw-r--r-- 1 root root   455 2010-08-05 08:50 gnome-screenshot.desktop
-rw-r--r-- 1 root root   461 2010-08-05 08:50 gnome-search-tool.desktop
-rw-r--r-- 1 root root   416 2010-10-04 13:34 gnome-settings-mouse.desktop
-rw-r--r-- 1 root root   439 2010-08-12 08:26 gnome-sound-recorder.desktop
-rw-r--r-- 1 root root   410 2010-09-27 12:24 gnome-sudoku.desktop
-rw-r--r-- 1 root root   457 2010-08-05 08:50 gnome-system-log.desktop
-rw-r--r-- 1 root root   458 2010-05-27 12:09 gnome-system-monitor.desktop
-rw-r--r-- 1 root root   471 2011-02-15 08:13 gnome-terminal.desktop
-rw-r--r-- 1 root root   520 2010-10-04 13:34 gnome-theme-installer.desktop
-rw-r--r-- 1 root root   435 2010-08-12 08:26 gnome-volume-control.desktop
-rw-r--r-- 1 root root   362 2010-09-27 12:45 gnome-wm.desktop
-rw-r--r-- 1 root root   377 2010-09-27 12:24 gnomine.desktop
-rw-r--r-- 1 root root   458 2010-08-12 08:26 gstreamer-properties.desktop
-rw-r--r-- 1 root root   379 2010-09-27 13:14 gucharmap.desktop
-rw-r--r-- 1 root root   336 2010-11-26 08:45 gwibber-accounts.desktop
-rw-r--r-- 1 root root   786 2010-11-26 08:45 gwibber.desktop
-rw-r--r-- 1 root root   310 2010-11-26 08:45 gwibber-preferences.desktop
-rw-r--r-- 1 root root   428 2010-07-28 19:07 hplj1020.desktop
-rw-r--r-- 1 root root   235 2010-11-16 13:20 ibus-setup.desktop
-rw-r--r-- 1 root root   581 2010-08-27 02:58 im-switch.desktop
-rw-r--r-- 1 root root  3385 2010-09-20 04:39 inkscape.desktop
-rw-r--r-- 1 root root   258 2010-11-23 17:08 jockey-gtk.desktop
-rw-r--r-- 1 root root   480 2010-10-04 13:34 keybinding.desktop
-rw-r--r-- 1 root root   445 2010-10-04 13:34 keyboard.desktop
-rw-r--r-- 1 root root  9339 2010-10-05 06:52 language-selector.desktop
-rw-r--r-- 1 root root  2558 2010-09-02 12:04 luckybackup.desktop
-rw-r--r-- 1 root root  2843 2010-09-02 12:04 luckybackup-gnome-su.desktop
-rw-r--r-- 1 root root  2884 2010-06-15 10:41 luckybackup-kde-su.desktop
-rw-r--r-- 1 root root   403 2010-09-27 12:23 mahjongg.desktop
-rw-r--r-- 1 root root   344 2010-10-21 12:30 manage-print-jobs.desktop
-rw-r--r-- 1 root root   504 2010-09-20 11:39 metacity.desktop
-rw-r--r-- 1 root root 17938 2011-02-15 07:31 mimeinfo.cache
-rw-r--r-- 1 root root  1031 2010-07-26 10:14 miro.desktop
-rw-r--r-- 1 root root   270 2010-07-05 04:40 monodoc.desktop
-rw-r--r-- 1 root root   343 2010-10-18 00:21 mount-archive.desktop
-rw-r--r-- 1 root root   395 2010-10-18 00:21 nautilus-autorun-software.desktop
-rw-r--r-- 1 root root   446 2010-10-18 00:21 nautilus-browser.desktop
-rw-r--r-- 1 root root   444 2010-10-18 00:21 nautilus-computer.desktop
-rw-r--r-- 1 root root   454 2011-02-15 08:14 nautilus.desktop
-rw-r--r-- 1 root root   466 2010-10-18 00:21 nautilus-file-management-properties.desktop
-rw-r--r-- 1 root root   459 2010-10-18 00:21 nautilus-folder-handler.desktop
-rw-r--r-- 1 root root   356 2010-10-18 00:21 nautilus-home.desktop
-rw-r--r-- 1 root root   278 2010-10-18 00:21 network-scheme.desktop
-rw-r--r-- 1 root root   456 2010-09-16 14:01 nm-connection-editor.desktop
-rw-r--r-- 1 root root   361 2010-09-27 05:08 onboard.desktop
-rw-r--r-- 1 root root   383 2010-09-27 05:08 onboard-settings.desktop
-rw-r--r-- 1 root root   390 2011-01-28 04:11 openjdk-6-java.desktop
-rw-r--r-- 1 root root   334 2011-01-28 04:11 openjdk-6-javaws.desktop
-rw-r--r-- 1 root root   294 2011-01-28 04:11 openjdk-6-policytool.desktop
-rw-r--r-- 1 root root  9194 2011-01-29 02:56 openoffice.org-calc.desktop
-rw-r--r-- 1 root root  6859 2011-01-29 02:56 openoffice.org-draw.desktop
-rw-r--r-- 1 root root  9038 2011-01-29 02:56 openoffice.org-impress.desktop
-rw-r--r-- 1 root root  7791 2011-01-29 02:56 openoffice.org-math.desktop
-rw-r--r-- 1 root root 10130 2011-01-29 02:56 openoffice.org-writer.desktop
-rw-r--r-- 1 root root   465 2010-09-27 19:34 orca.desktop
-rw-r--r-- 1 root root   290 2010-08-19 09:13 palimpsest.desktop
-rw-r--r-- 1 root root   334 2011-02-15 08:09 pidgin.desktop
-rw-r--r-- 1 root root   406 2010-10-15 09:46 pitivi.desktop
-rw-r--r-- 1 root root   220 2010-09-15 12:18 python2.6.desktop
-rw-r--r-- 1 root root   389 2010-09-27 12:25 quadrapassel.desktop
-rw-r--r-- 1 root root   679 2010-11-09 13:36 rhythmbox.desktop
-rw-r--r-- 1 root root   623 2010-11-09 13:36 rhythmbox-device.desktop
drwxr-xr-x 2 root root  4096 2010-10-07 12:10 screensavers
-rw-r--r-- 1 root root   424 2010-10-01 03:20 seahorse.desktop
-rw-r--r-- 1 root root   476 2010-09-27 12:45 session-properties.desktop
-rw-r--r-- 1 root root   481 2010-11-26 08:42 shares.desktop
-rw-r--r-- 1 root root   332 2010-09-30 09:56 shotwell.desktop
-rw-r--r-- 1 root root   997 2010-09-30 09:56 shotwell-viewer.desktop
-rw-r--r-- 1 root root   212 2010-10-22 04:00 simple-scan.desktop
-rw-r--r-- 1 root root   467 2010-09-20 12:22 software-properties-gtk.desktop
-rw-r--r-- 1 root root   500 2010-09-27 12:23 sol.desktop
-rw-r--r-- 1 root root   353 2010-09-20 20:23 synaptic.desktop
-rw-r--r-- 1 root root  6920 2010-09-20 20:23 synaptic-kde.desktop
-rw-r--r-- 1 root root   304 2010-10-21 12:30 system-config-printer.desktop
-rw-r--r-- 1 root root   404 2010-11-26 08:42 time.desktop
-rw-r--r-- 1 root root   353 2010-10-26 12:56 tomboy.desktop
-rw-r--r-- 1 root root  2311 2010-09-27 20:17 totem.desktop
-rw-r--r-- 1 root root   399 2011-02-15 08:07 transmission.desktop
-rw-r--r-- 1 root root   272 2010-08-25 00:55 tsclient.desktop
-rw-r--r-- 1 root root   258 2010-08-27 06:15 ubuntu-about.desktop
-rw-r--r-- 1 root root   348 2010-10-20 11:57 ubuntuone-preferences.desktop
-rw-r--r-- 1 root root   398 2010-12-03 11:34 ubuntu-software-center.desktop
-rw-r--r-- 1 root root   256 2010-11-12 09:44 update-manager.desktop
-rw-r--r-- 1 root root   288 2010-09-27 05:21 usb-creator-gtk.desktop
-rw-r--r-- 1 root root   403 2010-11-26 08:42 users.desktop
-rw-r--r-- 1 root root   403 2010-08-12 00:06 vinagre.desktop
-rw-r--r-- 1 root root   382 2010-08-12 00:06 vinagre-file.desktop
-rw-r--r-- 1 root root   453 2010-11-09 13:18 vino-preferences.desktop
-rw-r--r-- 1 root root   799 2011-01-18 14:58 virtualbox.desktop
-rw-r--r-- 1 root root  1087 2011-02-15 08:15 vlc.desktop
-rw-r--r-- 1 root root   446 2010-10-04 13:34 window-properties.desktop
-rw-r--r-- 1 root root  1373 2011-01-07 04:30 wine-browsedrive.desktop
-rw-r--r-- 1 root root  1211 2011-01-07 04:30 wine.desktop
-rw-r--r-- 1 root root  1075 2011-01-07 04:30 wine-notepad.desktop
-rw-r--r-- 1 root root  1795 2011-01-07 04:30 wine-uninstaller.desktop
-rw-r--r-- 1 root root  1832 2011-01-07 04:30 wine-winecfg.desktop
-rw-r--r-- 1 root root   351 2010-07-06 02:39 yelp.desktop

```

one of the first things i did was to chown that directory back to root.. btw the system is basically brand new. i installed it a few days ago. thanks for the help!

---

### Post by sikander3786 on 2011-02-16
Here is how they look on my system when I filter for nautilus.

```
-rw-r--r-- 1 root root   516 2010-06-25 18:01 brasero-nautilus.desktop
-rw-r--r-- 1 root root   395 2010-07-07 20:00 nautilus-autorun-software.desktop
-rw-r--r-- 1 root root   461 2010-07-07 20:00 nautilus-browser.desktop
-rw-r--r-- 1 root root   444 2010-07-07 20:00 nautilus-computer.desktop
-rw-r--r-- 1 root root   440 2010-07-07 20:00 nautilus.desktop
-rw-r--r-- 1 root root   481 2010-07-07 20:00 nautilus-file-management-properties.desktop
-rw-r--r-- 1 root root   459 2010-07-07 20:00 nautilus-folder-handler.desktop
-rw-r--r-- 1 root root   356 2010-07-07 20:00 nautilus-home.desktop

```

So, definitely it is a permission problem. And as you did a chown of the whole directory, your other applications might also be acting weird. In my opinion, if you don't have lots of customization and settings, re-install is the easier option here.

Or you can wait for some other opinions also for the sake of consensus.

---

### Post by Aaron.A on 2011-02-16
i do have a lot of custo. an alternative would be great, i really need to get some work done, and won't have time to do something like installing a new system =/ 
i guess i'll get another file manager for now. i managed to mount my drive by using the browser that pops up when you "open" from an app

---

### Post by Aaron.A on 2011-02-16
i'm using nautilus elementary, not sure if that matters but, if i remove nautilus entirely and reinstall would that perhaps fix it?

---

