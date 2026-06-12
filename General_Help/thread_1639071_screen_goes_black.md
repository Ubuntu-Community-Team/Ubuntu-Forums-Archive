---
title: "screen goes black"
date: 2010-12-06
forum: General Help
---

### Post by rmcellig on 2010-12-06
For some reason, when I watch movies be it Totem Movie player or VLC player, and even if I leave my computer for a few minutes, the screen goes black. I have to giggle the mouse for the screen to come back. What could be causing this and how can I fix it. My settings are disabled. Is there anything else I forgot to check?

I am using Ubuntu 10.10

---

### Post by sikander3786 on 2010-12-06
See if this one helps.

[http://ubuntuforums.org/showpost.php?p=10162899&postcount=14](http://ubuntuforums.org/showpost.php?p=10162899&postcount=14)

---

### Post by rmcellig on 2010-12-06
Thanks!!

Here is the code generated from the page you described in your previous post:

```

randy@randy-ubuntu:~$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
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
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
randy@randy-ubuntu:~$ 
```

---

### Post by sikander3786 on 2010-12-06
>   Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On


That seems pretty normal.

Screen saver is not configured to come up either then what is causing that blank screen/standby?

I would suggest to record the exact time-out for monitor standby. Is that periodic or just random?

---

### Post by rmcellig on 2010-12-06
I think it is periodic. So far the screen hasn't gone black. I will try to watch another video and see what happens. I will post back.

---

