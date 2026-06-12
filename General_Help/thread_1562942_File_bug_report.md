---
title: "File bug report?"
date: 2010-08-28
forum: General Help
---

### Post by jfreak_ on 2010-08-28
So whenever I start my system, my desktop effects are disabled. I want to file a bug repor(I couldn't find any existing bug report)t but how do I know which program is causing this and also how can I run ubuntu-bug for this since the bug happens during restart.

---

### Post by geirha on 2010-08-28
If  System -> Preferences -> Appearance -> Visual Effects is set to None, it will not enable compiz when you log in. Note though, that setting it to Normal or Extra will wipe out any custom compiz configuration you may have set, so export your current config (using ccsm), set Visual Effects to Normal, then import your config again.

---

### Post by jfreak_ on 2010-08-28
Well yeah thats the problem. I always keep the visual effects to extra and when i restart it goes back to none. So basically everytime i start my system first i have to set it to extra from none

---

### Post by geirha on 2010-08-28
If you log out and back in again (as opposed to restarting the system), does it revert back to none then as well? 

It sounds like, for whatever reason, the settings aren't saved properly when your gnome-session closes.

---

### Post by jfreak_ on 2010-08-28
Yes it reverts to none on logging out and logging in

---

### Post by geirha on 2010-08-28
Do you see any permission denied errors or similar in ~/.xession-errors ? It could be a file or directory it needs to write to is not writable, and thus it's unable to save your settings on log out.

---

### Post by jfreak_ on 2010-08-28
hmmm no permission denied errors but there are errors which I think might be related

sh: /usr/bin/nvidia-settings: not found
.
.
.
.

(gnome-appearance-properties:4930): Gtk-WARNING **: Unable to locate theme engine in module_path: "aurora",

(gnome-appearance-properties:4930): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
There is no available graphics driver for your system which supports the composite extension, or the current one already supports it.

---

### Post by jfreak_ on 2010-08-29
bumpity bump

---

### Post by geirha on 2010-08-30
This looks similar [https://bugs.launchpad.net/ubuntu/+bug/563023](https://bugs.launchpad.net/ubuntu/+bug/563023)

---

### Post by jfreak_ on 2010-08-30
somewhat similar, but there is no hanging or any other problem after enabling 'extra'. Its only that I have to enable it every time I boot . So should I file a bug? If yes , with what?

---

### Post by realzippy on 2010-08-30
Make your compiz settings in CCSM,and do not mark any checkbox in visual effects.Then add 
```
compiz --replace
```
in your startup applications and it should work...

---

### Post by jfreak_ on 2010-08-30
@realzippy
That worked thanks

---

