---
title: "Clutterflow in Nautilus Elementary in Maverick not working"
date: 2010-10-10
forum: General Help
---

### Post by tariqsheikh on 2010-10-10
I have been using Maverick since the release candidate was released. I also installed nautilus elementary (the latest version). The inbuilt terminal works great, but the clutterflow option in the view menu only brings up a blank black screen with the file name only (please see [http://ubuntuone.com/p/JSY/](http://ubuntuone.com/p/JSY/)). I couldn't find help anywhere else. Any help would be appreciated.

The terminal gives this:


** Message: action_show_hide_clutter_callback
** Message: nautilus_window_slot_show_clutter
fm_icon_get_clutter_widget
create_icon_clutter
** Message: model_icon_added
fill_visible_items::file:///root/Desktop 0
ADDED: file:///root/Desktop 0 index:7
** Message: ADD AT POS: 0 FRONT 0
fill_visible_items::file:///root/Downloads 1
ADDED: file:///root/Downloads 1 index:8
** Message: ADD AT POS: 0 FRONT 0
** Message: model_icon_added
** Message: items_icon_update
REUSE: file:///root/Desktop 0 dist:0 index:7
REUSE: file:///root/Downloads 1 dist:1 index:8
** Message: Restack

I am using Ubuntu Netbook Edition on a Dell Inspiron mini 1012.

---

### Post by ammonkey on 2010-10-10
Hello,
It's a know bug with intel hardware, same occur with Unity.
Add "export CLUTTER_VBLANK=none" to /etc/environment (without the quotes)

---

### Post by tariqsheikh on 2010-10-10
> **ammonkey said:**
> Hello,
It's a know bug with intel hardware, same occur with Unity.
Add "export CLUTTER_VBLANK=none" to /etc/environment (without the quotes)
Wow, thanks a lot. It worked like a charm.
Animation is a bit slow though. I guess it is because of the Intel hardware.

---

### Post by jdorenbush on 2011-04-09
Thanks for the fix! Worked perfect.

---

### Post by buzzing_bee on 2011-07-11
well that's solve my problem too :)

---

### Post by StepNjump on 2011-12-09
Doesn't work for me though....
After adding the line, I tried nautilus -q, even rebooted. Nothing.

Could it be anything else?

---

