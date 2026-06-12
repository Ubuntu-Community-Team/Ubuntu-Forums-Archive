---
title: "My laptop is booting into KDE for some reason."
date: 2011-05-23
forum: General Help
---

### Post by Maheriano on 2011-05-23
Last week I installed Zoneminder so I can have some webcam security and I let it run on Mocord (motion detection record) for 24 hours just to see how it worked and run some tests. After that 24 hours I changed it to Monitor so that it wouldn't record anything and wouldn't fill up my 320 gig drive but even after I did that the webcam LED stayed on. Not sure if this is normal, I guess it is since it is still using the webcam, just not recording. I don't think.

2 nights ago I was using it to watch videos online and it was a little slow but was still good enough.

This morning I unplugged it and brought it downstairs to use it but when I opened the lid the hard drive LED was constant and the mouse was all jumpy. Anything I clicked on took a minute to register and the disk utility that I tried loading 2 days earlier looked like it was still loading. I couldn't click anything because the hard drive was running like crazy. Or processor or whatever that light is.

So I held the power button, rebooted and nothing on the menu bar was loaded and the hard drive was going crazy again, still couldn't click on anything. So I rebooted again and this time it gave me a popup before the desktop loaded:
> There is a problem with the configuration server.
(/usr/lib/libgconf2-4/conf-sanity-check-2 extend with status 256)
So I click Close and it boots to a black background with huge icons and there are obviously no drivers loaded. There's now a new error message:
> 
GConf error: Faield to contact configuration server: the most common cause is a missing or misconfigured D-Bus session bus daemon. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details - 1: GetIOR faield: GDBus.Error: org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process /usr/lib/libgconf2-4/gconfd-2 received signal 6)

All further errors shown only on terminal.


And then it does nothing, all the menus say KDE. Though thankfully my hard drive is not going nuts anymore. Webcam LED is still on though since Zoneminder runs as a service on Apache.

It's a dual core Dell Studio 15 laptop with all the newest updates and I have 3 separate partitions on my install: /, /home, SWAP. My / partition has 2 gigs free according to KDE and my /home partition has 124 gigs free.

---

### Post by Maheriano on 2011-05-23
I booted to a command prompt and tried to reinstall gdm but it told me there was no space left on the device. So I went into /usr/share/zoneminder/events/main and deleted everything in there through the command line. It looks like the Zoneminder events had filled up my hard drive. After that I rebooted into Ubuntu fine except for an error message about gdm. So I ran "sudo apt-get install --reinstall gdm" and I'm just waiting for it to finish now.

---

