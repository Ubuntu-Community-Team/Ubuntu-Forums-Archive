---
title: "Problems with installing/reinstalling Gimp - need help please!"
date: 2010-08-18
forum: General Help
---

### Post by tgeer43 on 2010-08-18
Ok, I've really borked up my Gimp. I'm running 10.04 64-bit and had at some point installed gimp but don't recall how or where I got it from. The strange part is that neither Synaptic or Ubuntu Software Center showed it as being installed.

Anyway, it started misbehaving (locking up) so I figured I'd uninstall and reinstall. That's when I discovered that the system didn't show it as being installed at all. Needless to say, I couldn't uninstall it so I decided to just reinstall over the top through Ubuntu Software Center. The installation seemed to complete normally but when I tried running it I got an error stating that there was a version mismatch for libgimp and suggesting that maybe I had gimp installed in both /usr and /usr/local. Not knowing what else to do, I uninstalled via Ubuntu Software Center and then removed all gimp related files from both /usr and /usr/local. Lastly, I reinstalled again via the Software Center.

Now when I try to launch gimp I get a box in the panel's Window List titled "Starting Gimp Image Editor" but shortly thereafter it disappears and I'm back to the desktop. I've even tried it all over again but utilizing Synaptic for the final install (as well as apt-get) with the same result - it tries to load and then... nothing.

I must have deleted something essential when rooting around in /usr and /usr/local that is not replaced by reinstalling gimp but I have no idea what or where.

So now what do I do? I really need gimp installed on this machine. I do have a full system backup but it's a couple of weeks old and I don't want to lose all of the changes that I've made to the system since then.

Any assistance would be greatly appreciated.

Regards,

tgeer

---

### Post by jack_hmr on 2010-08-24
Please open a terminal, type in ```
gimp
```, hit enter, and then post back with whatever the terminal output is.

---

### Post by dFlyer on 2010-08-24
Have you tried deleting .gimp from your home directory?

---

### Post by tgeer43 on 2010-08-26
Thanks for the replies, guys.

dFlyer: My home directory had both .gimp-2.6 and a .gimp-2.7 folders. I deleted both of them but still no joy. :(

jack_hmr: Entering 'gimp' or 'gimp-2.6' in the console both produce the following output:

```
tgeer@teg-02:~$ gimp
(gimp:1518): GLib-GObject-WARNING **: specified class size for type `GimpOperationPointFilter' is smaller than the parent type's `GeglOperationPointFilter' class size
(gimp:1518): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(gimp:1518): GLib-GObject-CRITICAL **: g_type_register_static: assertion `parent_type > 0' failed
(gimp:1518): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
(gimp:1518): GLib-GObject-WARNING **: cannot retrieve class for invalid (unclassed) type `<invalid>'
```Based on this I made sure that the requisite gegl and glib packages were installed but this resulted in no change. I'm pretty well stumped at this point but not willing to give up.

As a temporary stop-gap measure I install Pinta which handles *most* of my graphic editing needs but I still want my gimp!

Thanks again.

Regards,

tgeer

---

### Post by pbrane on 2010-08-26
I take it you found some gimp 2.7 stuff in */usr/local*. Did you also look in */usr/local/share/* and */usr/local/etc/*for any gimp related stuff? I don't think gimp 2.7 came from the official repos so you must have installed it from source or some other non-deb package. You may have to search all the system directories looking for gimp files to fix this.

---

