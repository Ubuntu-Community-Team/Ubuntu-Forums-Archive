---
title: "Configuring screen blanking"
date: 2011-05-27
forum: General Help
---

### Post by Ouroborus777 on 2011-05-27
In Ubuntu is seems the power saving features correctly change things so that xset sees them. But not with the screensaver stuff. I'm aware of the bazillion posts asking how to turn off or adjust screen blanking. It seems none of these explain why the screen blanking settings do not seem to be fully configurable via the gui.

Specifically, where in the gui does one change or disable the screen blanking feature? (What otherwise would be controlled via 'xset s'.)

(In my opinion, adding an entry to the Startup Applications list is not the proper way to do this sort of thing. It really should be configurable via Preferences > Screensaver or  Preferences > Power Management. If it's somewhere else in the Preferences settings, I'd love to know where.)

This is what 'xset q' shows me:
```
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 7200    Suspend: 7200    Off: 14400
  DPMS is Disabled
```This is with power management turned off via Preferences > Power Management > On AC Power

Under Preferences > Screensaver:
"Screensaver theme" is set to "Blank Screen"
"Regard the computer as idle" is set to 1 minute
"Activate screensaver when computer is idle" and "Lock screen when screensaver is active" are both unchecked.

---

### Post by 73ckn797 on 2011-05-27
Have you tried the "configuration editor"? There are tweaks in there for power management. It resides in Applications/System. If it is not listed then use System/Preferences/Main Menu to "turn it on."

---

### Post by Ouroborus777 on 2011-05-27
> **73ckn797 said:**
> Have you tried the "configuration editor"? There are tweaks in there for power management. It resides in Applications/System. If it is not listed then use System/Preferences/Main Menu to "turn it on."

There doesn't seem to be anything here that isn't already configurable with the appropriate apps. I don't see anything here that might resolve the screen blanking issue.

---

### Post by 73ckn797 on 2011-05-27
Under power management/AC Power/Display, is it set to put display to sleep "never"?

---

### Post by Ouroborus777 on 2011-05-27
> **73ckn797 said:**
> Under power management/AC Power/Display, is it set to put display to sleep "never"?

It is set to "Never" but the screen still blanks.

---

