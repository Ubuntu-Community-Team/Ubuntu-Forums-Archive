---
title: "Fail to start gnome/kde"
date: 2006-05-13
forum: General Help
---

### Post by rittub on 2006-05-13
Hi!
My system returns to the login screen after I entered password. I can log in to the fail-safe mode and I can get into gnome by entering "gnome-session" in terminal. 
" (gnome-cups-icon:8155): WARNING **: IPP request failed with status 1030" keeps poping up every 2 seconds in terminal.
I don't have any printer connected.

Please help, thanks in advance.

The following messages are returned in terminal:
```
mai@ubuntu:~$ gnome-session
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/ubuntu:/tmp/.ICE-unix/8073

** (gnome-session:8073): WARNING **: Host name lookup failure on localhost.
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
manager.c/562: setting[0]: bool: autobrowse = 1
manager.c/562: setting[1]: bool: autoburn = 1
manager.c/557: setting[2]: string: autoburn_audio_cd_command = serpentine
manager.c/557: setting[3]: string: autoburn_photo_cd_command = nautilus --no-desktop burn:
manager.c/557: setting[4]: string: autoburn_data_cd_command = nautilus --no-desktop burn:
manager.c/562: setting[5]: bool: autoipod = 0
manager.c/557: setting[6]: string: autoipod_command =
manager.c/562: setting[7]: bool: automount_drives = 1
manager.c/562: setting[8]: bool: automount_media = 1
manager.c/562: setting[9]: bool: autophoto = 1
manager.c/557: setting[10]: string: autophoto_command = gnome-volume-manager-gthumb %h
manager.c/562: setting[11]: bool: autoplay_cda = 1
manager.c/557: setting[12]: string: autoplay_cda_command = sound-juicer -d %d
manager.c/562: setting[13]: bool: autoplay_dvd = 1
manager.c/557: setting[14]: string: autoplay_dvd_command = totem %d
manager.c/562: setting[15]: bool: autoplay_vcd = 1
manager.c/557: setting[16]: string: autoplay_vcd_command = totem %d
manager.c/562: setting[17]: bool: autoprinter = 0
manager.c/557: setting[18]: string: autoprinter_command = gnome-cups-add hal://%h
manager.c/562: setting[19]: bool: autorun = 0
manager.c/557: setting[20]: string: autorun_path = .autorun:autorun:autorun.sh
manager.c/557: setting[21]: string: eject_command = /usr/bin/eject
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
/usr/bin/gnome-session(8153): libnotify: Error connecting to session bus: Unable to determine the address of the message bus
/usr/bin/gnome-session(8153): libnotify: Error connecting to session bus: Unable to determine the address of the message bus

** (gnome-cups-icon:8155): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8155): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8155): WARNING **: IPP request failed with status 1030

** (gnome-cups-icon:8155): WARNING **: IPP request failed with status 1030

...

```

Here are xsession-errors:
```
Xsession: X session started for mai at Sat May 13 20:11:38 EDT 2006

(gnome-terminal:8027): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8027): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8027): Gtk-CRITICAL **: gtk_style_finalize: assertion `style->attach_count == 0' failed

```

---

### Post by rittub on 2006-05-14
I completely removed cupsys and reinstalled it. It's working fine now.

---

