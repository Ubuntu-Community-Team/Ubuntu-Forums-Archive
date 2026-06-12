---
title: "Ubuntu 11.10 only showing wallpaper after startup"
date: 2011-11-03
forum: General Help
---

### Post by movin on 2011-11-03
I'm using Ubuntu 11.10 pretty much as it comes after the upgrade. The other night I was trying to install gCDEmu and getting it to work (maybe I happened to break something then). Ever since when I start the computer, only the purplish wallpaper, without icons, is visible. It should also be noted that as the system is starting, just after the login-melody, the icons from the panel on the left are briefly visible, and then disappear forever.

I've been trying to find some solutions online, which led me to try "gnome-panel" in the terminal I still can open with ctrl+alt+F1, which gets me the message: 

> (gnome-panel:1909): Gtk-WARNING **: cannotopen display:Further googling (on another computer), suggested I try "export DISPLAY=:0", which I did. Following that command, "gnome-panel" renders the following message:

> (gnome-panel:2170): GLib-GObject-WARNING **: /build/build/glib2.0-2.30.0/./gobject/gsignal.c:2295: signal 'size_request' is invalid for instance '0x7f81680c13f0'
gnome-panel: symbol lookup error: gnome-panel: undefined symbol: gtk_drag_source_set_icon_giconAnd for these lines I couldn't really find any solution from googling, so I figured I'd make a thread here. Please bear in mind that I'm fairly unskilled, so if I need to fetch any additional information in order for you to be able to help me, please also mention where I can find it.

Many thanks in advance!

---

### Post by movin on 2011-11-03
Now realizing I'm not using gnome, but Unity, my own attempts at solving the problem of course seem rather laughable. Nevertheless, the problem is as I described it above...

---

### Post by gandaran on 2011-11-03
that is a compiz problem, try this command
```
unity --reset
```
if it doesn't fix it login to unity 2D instead then delete all the home user compiz settings and reboot you'll have the unity 3D back.

---

### Post by movin on 2011-11-03
> **gandaran said:**
> that is a compiz problem, try this command
```
unity --reset
```if it doesn't fix it login to unity 2D instead then delete all the home user compiz settings and reboot you'll have the unity 3D back.

Thanks for the reply, however it did not solve the problem. I'm not sure if you get compiz by default, but either way, I did an apt-get install it after I had already got this problem, since I read about it online. Hence I might have had the problem longer than I had compiz.

I also tried your suggestions; reseting, removing and reinstalling Unity and compiz in different orders, didn't really help. I also specifically tried to remove the compiz settings by using locate on the files that are in the home-folder, and managed to remove most of them, but to no avail.

Trying to start unity-panel-service manually with /usr/lib/unity/unity-panel-service, I first - again - got the > Gtk-WARNING **: cannot open display:
As before, I tried export DISPLAY=:0 and then repeated the unity-panel-service command, resulting in the following:

> ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libmessaging.so ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libpower.so ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libsession.so (unity-panel-service:2399): Indicator-Session-DEBUG: get entries ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libapplication.so ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libappmenu.so ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libdatetime.so (unity-panel-service:2399): Indicator-Datetime-DEBUG: Evaluating bitmask for '%a %b %e %l:%M %p' (unity-panel-service:2399): Indicator-Datetime-DEBUG: Checking against 168 possible times (unity-panel-service:2399): Indicator-Datetime-DEBUG: Guessing max time width: 146 ** (unity-panel-service:2399): DEBUG: Loading: /usr/lib/indicators3/6/libsoundmenu.so ** (unity-panel-service:2399): DEBUG: on_bus_acquired ** (unity-panel-service:2399): DEBUG: on_name_lost For some reason that quote does not fully show the messages I see on the screen. Among the missing ones are:
> 
(unity-panel-service:2399) GLib-CRITICAL **: g_error_free: assertion 'error != NULL' failed

Any further ideas on what I can do? Would be greatly appreciated!

---

