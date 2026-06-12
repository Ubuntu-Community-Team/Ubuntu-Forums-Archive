---
title: "Disable XF86Search feature / key"
date: 2010-02-05
forum: General Help
---

### Post by SadaraX on 2010-02-05
I want to disable the XF86Search feature in my system. I will try anything. 

One of my mouse buttons, when pressed, triggers this XF86Search no matter what I disable or change. (This feature opens up my browser and goes to a search page.) Strangely the mouse button is being interpreted as a key, not a mouse-button press. (This actually may be a bug in Ubuntu...)

How do I disable this feature?

I am running KDE 4.3.5 with Ubuntu 9.10 Karmic (Kubuntu). Though I use BTNX to configure my mouse buttons, this feature has absolutely nothing to do with that. I have tested by disabling BTNX completely and clicking this special button on my mouse still loads a search page.

Here is the xev command output:

```

.....
KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   2   0   0   0

KeyRelease event, serial 36, synthetic NO, window 0x3a00001,
    root 0x13c, subw 0x0, time 32389848, (402,274), root:(408,295),
    state 0x0, keycode 225 (keysym 0x1008ff1b, XF86Search), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

ClientMessage event, serial 36, synthetic YES, window 0x3a00001,
    message_type 0xf6 (WM_PROTOCOLS), format 32, message 0xf7 (WM_DELETE_WINDOW)
... # This was the end of the output.

```

EDIT/UPDATE: It seems I was mistaken. The problem is not universal, just limited to KDE. Unfortunately I cannot change that thread property.

---

### Post by audiomick on 2010-02-05
> **SadaraX said:**
>  (This feature opens up my browser and goes to a search page.) Strangely the mouse button is being interpreted as a [COLOR=Red]key, not a mouse-button press.[/COLOR] 
Should you not then be looking at your keyboard shortcut setup? I don't know where that is in KDE, but it will be there somewhere...

---

### Post by SadaraX on 2010-02-05
> **audiomick said:**
> Should you not then be looking at your keyboard shortcut setup? I don't know where that is in KDE, but it will be there somewhere...

I have looked extensively, both with a variety of global configuration files throughout the system, and through the control managers provided by KDE. I have found nothing that even remotely references this.

---

