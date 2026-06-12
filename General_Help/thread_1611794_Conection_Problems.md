---
title: "Conection Problems"
date: 2010-11-02
forum: General Help
---

### Post by bizkyt on 2010-11-02
Hello,

I have some problems with network-manager. After I deleted it with synaptic, and removed some directories from /usr/local with "network-manager" and "nm-*" files, I can't use network-manager again.
I tried to completely remove network-manager from synaptic, reboot and then installed again (network-manager-gnome too), reboot it and the applet don't appear in tray, even if I add it to start up apps, and add notification area in tray icon.
I put in console "nm-applet" and the outpout:

> 
(nm-applet:1992): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:2275: signal `permission-changed' is invalid for instance `0x11885c0'
nm-applet: symbol lookup error: nm-applet: undefined symbol: nm_client_get_permission_result


I tried everything, what can I do now?

---

### Post by bizkyt on 2010-11-02
I made this commands in console (read in a website something related to my problem):

> 
sudo cp -f /usr/lib/libnm-util.so.1* /usr/local/lib/
sudo cp -f /usr/lib/libnm-util.so.1* /usr/local/lib/


And the nm-applet comes to notification area tray again. But now problems again. It says in my language something like network-manager not started like in the screenshot:

[IMG]http://img135.imageshack.us/img135/5909/capturaecra1.png[/IMG]


I tried again reinstalled network-manager and network-manager-gnome and nothing happens ..

---

### Post by bizkyt on 2010-11-02
I made a fresh installation of ubuntu to resolve this.

---

