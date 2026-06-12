---
title: "DDC Disable Removed from Intel Video Drivers"
date: 2009-10-28
forum: General Help
---

### Post by SDNick484 on 2009-10-28
Tonight I upgraded to Karmic, but before I could really take it for a spin I ran into one significant issue.  The Intel 2.9.0 drivers no longer accept:
```
Option          "DDC"           "false"
```
to disable [DDC]("http://en.wikipedia.org/wiki/Display_Data_Channel") detection over HDMI.  This is a significant issue for be because my "monitor" is actually a 47" Vizio 1080P HDTV that unfortunately declares itself as a Vizio 50" with a max resolution of 1280x720.  For 8.10 and 9.04, I'd been able to disable DDC detection and manually supply a modeline in my xorg.conf, however Karmic ignores the option and forces me to use DDC.

I resolved the issue via the following xrandr commands:
```
$ xrandr --newmode "1920x1080" 148.35 1920 2008 2052 2200 1080 1085 1090 1125 +hsync +vsync
$ xrandr --addmode HDMI1 "1920x1080"
$ xrandr --output HDMI1 --mode "1920x1080"

```

Although it's a hack, I created a script with those commands and added it to the list of startup applications for Gnome (under System->Preferences).

Now your actual values for your specific 1080P TV/monitor may vary, so please be careful when specifying modelines.  Anyways, I hope this helps anyone else in a similar situation.  Folks with the older i810 and i815 drivers can still use the disable DDC, so this mainly applies to the i915 users (of which there's a lot) with devices that provide bad DDC information (which I hope is a small subset).

---

### Post by cariboo on 2009-11-07
A bump for the move.

---

### Post by Ms_Angel_D on 2009-11-07
> **cariboo907 said:**
> A bump for the move.

Thanks for moving the thread cariboo907



> **SDNick484 said:**
> Tonight I upgraded to Karmic, but before I could really take it for a spin I ran into one significant issue.  The Intel 2.9.0 drivers no longer accept:
```
Option          "DDC"           "false"
```
to disable [DDC]("http://en.wikipedia.org/wiki/Display_Data_Channel") detection over HDMI.  This is a significant issue for be because my "monitor" is actually a 47" Vizio 1080P HDTV that unfortunately declares itself as a Vizio 50" with a max resolution of 1280x720.  For 8.10 and 9.04, I'd been able to disable DDC detection and manually supply a modeline in my xorg.conf, however Karmic ignores the option and forces me to use DDC.

I resolved the issue via the following xrandr commands:
```
$ xrandr --newmode "1920x1080" 148.35 1920 2008 2052 2200 1080 1085 1090 1125 +hsync +vsync
$ xrandr --addmode HDMI1 "1920x1080"
$ xrandr --output HDMI1 --mode "1920x1080"

```

Although it's a hack, I created a script with those commands and added it to the list of startup applications for Gnome (under System->Preferences).

Now your actual values for your specific 1080P TV/monitor may vary, so please be careful when specifying modelines.  Anyways, I hope this helps anyone else in a similar situation.  Folks with the older i810 and i815 drivers can still use the disable DDC, so this mainly applies to the i915 users (of which there's a lot) with devices that provide bad DDC information (which I hope is a small subset).

SDNick484, How would somebody go about finding the lines needed for their own setup? I would really like to to get boxee working again on my laptop without reverting to jaunty. Thanks in advance,

Angel

---

