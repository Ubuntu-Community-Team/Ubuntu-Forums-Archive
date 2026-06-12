---
title: "No Touchpad Tab in Mouse Settings"
date: 2010-07-09
forum: General Help
---

### Post by balisada on 2010-07-09
I bought an Acer Aspire One Netbook and installed Ubuntu Netbook Remix, but the Touchpad tab in the mouse settings is missing.

How do I enable it?

I am using Ubuntu 10.04 (Lucid).

Thanks.


Balisada

---

### Post by Halfling Rogue on 2010-07-31
Same problem on an Asus K70IC. Would reaaally like to be able to disable the touchpad click; it keeps selecting when I don't want it to.

---

### Post by kerry_s on 2010-07-31
try installing "gpointing-device-settings".

you can also put "synclient TapButton1=0" in your startup instead.

---

### Post by Halfling Rogue on 2010-07-31
Tried gpointing, but it only shows the option for a wheel mouse, which hasn't ever been connected to the laptop.

Which startup file does that go in?

---

### Post by kerry_s on 2010-07-31
> **Halfling Rogue said:**
> Tried gpointing, but it only shows the option for a wheel mouse, which hasn't ever been connected to the laptop.

Which startup file does that go in?

system-> preferences-> startup applications

run it from a terminal first to check it works. 
accessories-> terminal

---

### Post by Halfling Rogue on 2010-08-03
> **kerry_s said:**
> system-> preferences-> startup applications

run it from a terminal first to check it works. 
accessories-> terminal

"Couldn't find synaptics properties. No synaptics driver loaded?"

I take it gsynaptics is the package I need here?

---

### Post by Halfling Rogue on 2010-08-07
Bump de-bump.

---

### Post by kerry_s on 2010-08-07
> **Halfling Rogue said:**
> "Couldn't find synaptics properties. No synaptics driver loaded?"

I take it gsynaptics is the package I need here?

that means your touchpad is reading as a normal ps2 type mouse instead of a touchpad.

---

### Post by Halfling Rogue on 2010-08-07
Well that's bizarre. Is there a way to fix it?

---

### Post by kerry_s on 2010-08-07
> **Halfling Rogue said:**
> Well that's bizarre. Is there a way to fix it?

i'm sure there is, but i don't know how. try hitting up google with your aspire 1 model #, i'm sure some 1 has had to have dealt with that.

---

### Post by field64 on 2013-03-10
I just installed Ubuntu 12.04.2 LTS on an Acer Aspire M notebook.

Several other forum and Internet articles pointed to kernel module psmouse, which drives the touchpad, if
the IMPS protocol option is enabled, this system-setting ->mouse/touchpad tab "touchpad" is not present.

If I load the module without the "proto=imps", the tab is again present, and appears to work

cat /etc/modprobe.d/touchpad.conf 
#options psmouse proto=imps
options psmouse 

Now to figure out why the Acer Aspire M touchpad is flaky, pointing inaccurate.

---

