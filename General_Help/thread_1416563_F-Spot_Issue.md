---
title: "F-Spot Issue"
date: 2010-02-26
forum: General Help
---

### Post by gallifrey on 2010-02-26
Hello,
        when I first installed Ubuntu (Karmic, x86), I removed the install of F-Spot via the Software Centre. 

I just tried reinstalling it, and the install went fine. Then I tried running it. The window flashed up for a second, then disappeared. It does this every time I try to run it, even after a cold boot. I have uninstalled and reinstalled several times, using USC, Synaptic, and apt-get. Always with the same result.

I tried running it from terminal using sudo, and got the following output:
[B]
anyuser@anycomputer:~$ sudo f-spot
[sudo] password for anyuser: 
** No session dbus found. Starting one **

(/usr/lib/f-spot/f-spot.exe:9598): GLib-WARNING **: g_set_prgname() called multiple times
[Info  13:35:49.606] Initializing DBus
[Info  13:35:49.732] Initializing Mono.Addins
[Info  13:35:49.975] Starting new FSpot server (f-spot 0.6.1.5)

** (/usr/lib/f-spot/f-spot.exe:9598): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:9598): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:9598): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:9598): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (/usr/lib/f-spot/f-spot.exe:9598): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  13:35:50.963] Starting BeagleService
[Info  13:35:50.982] Hack for gnome-settings-daemon engaged

(/usr/lib/f-spot/f-spot.exe:9598): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.[/B]

Can anybody make any sense of this?? Am I missing some dependency? 

any help would be greatly appreciated.

---

### Post by julipanno on 2010-02-26
The messages you are seeing are probably not related to F-Spot not starting. I get the same terminal output, and F-Spot starts fine.

I suggest removing the config files for F-Spot. These are located in 
~/.config/f-spot/
~/.gconf/apps/f-spot/
If you haven't already tried so, you could try 'sudo aptitude purge f-spot', which should automatically remove all configurations as well, and then reinstall it.

---

### Post by gallifrey on 2010-02-26
Thank you so much! That worked like a charm!

---

