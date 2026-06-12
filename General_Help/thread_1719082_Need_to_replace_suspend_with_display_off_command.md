---
title: "Need to replace suspend with display off command"
date: 2011-04-01
forum: General Help
---

### Post by age6racer on 2011-04-01
Hi all,

I've been searching for hours for a solution but cannot find it.

I have a tablet PC and I want to be able to toggle the screen ON/OFF using the power button on the top (like an iphone does)

A single short press of the button trigger standby/suspend and with gnome-power-manager or gconf-editor I can alter this to hibernate or shutdown but I really need to just kill the display and backlight with dpms.

I have dug into gconf-editor but I don't think it will let me replace any of the options with the command 

```
xset dpms force off
```

Is there some way I can divert to a script which executes my dpms command instead of carrying out a suspend?

---

### Post by age6racer on 2011-04-01
Does anyone here know more than I do about acpi events?

It seems that Ubuntu 10.10 has a rather complicated power/shutdown/suspend/hibernate setup..

I have been reading man pages, articles and threads on this all day now and as far as I can tell there is more than one system controlling things.

I have been hacking away at acpi files but nothing I do seems to change the behaviour of the suspend button.

In fact I'm not even sure that the files I'm editing are for the suspend button at all any more. Is there a separate sleep button on some systems?

I just need to send "xset dpms force off" in place of the suspend command when the button on the tablet is pressed. 

It can't be that hard!?

---

### Post by age6racer on 2011-04-01
Man it's lonely in this thread..
:(

---

