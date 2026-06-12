---
title: "Problem with touchpad and dual head and nautilus"
date: 2009-11-08
forum: General Help
---

### Post by mp3guy on 2009-11-08
Hi, 

I've got a laptop running Karmic 9.10, it's an Asus F5SR. 

First problem is with the touch pad: I can't disable it. I've tried following the instructions involving SHMConfig, using the different syndaemon commands, but as soon as I disable it, it gets renabled after a few seconds (after I move the mouse between my dual screen setup).

Secondly, I've got an ATI Radeon 3400HD. I set it up for dual head using fglrx and the ATI catalyst control centre, but I'm having terrible page tearing problems (yes v-sync is enabled) and also, if I disable desktop effects, whenever I run certain programs, like wine, the window decorations disappear and all the windows on the screen keep flickering on and off. 

Finally, with nautilus, if I try right clicking on a file and choosing properties nautilus crashes, with the following error message printed to terminal: 

```

(nautilus:18419): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

**
Eel:ERROR:eel-wrap-table.c:494:wrap_table_get_num_fitting: assertion failed: (max_child_size > 0)
Aborted

```

So far Karmic is very disappointing, I had problems with network manager causing random freezes every now and then. Has anyone got any solutions to any of these 3 (very annoying) problems?

---

### Post by mp3guy on 2009-11-09
Bump

---

