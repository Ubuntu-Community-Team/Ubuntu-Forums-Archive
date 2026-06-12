---
title: "Disable screen blanking / screensaver / power management"
date: 2011-11-28
forum: General Help
---

### Post by apoth on 2011-11-28
Since about 6 months ago, every 10 minutes or so my screen goes black, on a machine we use for our main TV viewing.

I'm pretty sick of repeatedly hacking around with commands and preference GUIs trying to stop this happening, with updates repeatedly knackering it and then having to blindly bash around trying to prevent it again.

This is a serious regression in my view - does anyone have a cure? (Short of OSX hopefully)

---

### Post by stinkeye on 2011-11-28
Put
```
xset -dpms
```
into startup applications.

or if that doesn't work try this script added to startup.
```
#!/bin/bash
sleep 10 &&
xset -dpms
xset s off
```

---

### Post by apoth on 2011-11-29
Thanks, but there's this:

```
$ sudo xset -dpms
server does not have extension for -dpms option
```

and xset s off doesn't seem to affect behaviour.

---

### Post by stinkeye on 2011-11-29
> **apoth said:**
> Thanks, but there's this:

```
$ sudo xset -dpms
server does not have extension for -dpms option
```

and xset s off doesn't seem to affect behaviour.

I don't know what that means.
If I input xset -q
I get this...
```
glen@Oneiric:~$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  33
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  **DPMS is Disabled**
```

---

### Post by apoth on 2011-11-29
```
 xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Shift Lock:  off
    03: Group 2:     off    04: Mouse Keys:  off    05: Scroll Lock: off
  auto repeat delay:  525    repeat rate:  11
  auto repeating keys:  ffffffffffffff7f
                        00ffffffffffffff
                        ffffffffffffffff
                        ffffffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  no    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x21    BlackPixel:  0    WhitePixel:  32767
Font Path:
  /usr/X11/lib/X11/fonts/misc/,/usr/X11/lib/X11/fonts/TTF/,/usr/X11/lib/X11/fonts/OTF,/usr/X11/lib/X11/fonts/Type1/,/usr/X11/lib/X11/fonts/75dpi/:unscaled,/usr/X11/lib/X11/fonts/100dpi/:unscaled,/usr/X11/lib/X11/fonts/75dpi/,/usr/X11/lib/X11/fonts/100dpi/,/Library/Fonts,/System/Library/Fonts
DPMS (Energy Star):
  Server does not have the DPMS Extension

```

---

### Post by stinkeye on 2011-11-30
This used to work but it appears even with DPMS is Disabled 
my screen still blanks.
I uninstalled the screensaver and checked the screen settings and bios but
still happens.
So I really have no idea now.

---

