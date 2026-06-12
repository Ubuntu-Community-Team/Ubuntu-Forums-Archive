---
title: "Power settings make no difference"
date: 2012-08-10
forum: General Help
---

### Post by p3aul on 2012-08-10
Ubuntu 10.04 64bit
Gnome 2.30.2
Nautilus 2.30.1


I guess I live in a very small universe because "Never" seems to be about 15 minutes. IN "Power Management => On AC Power" the options are set to "Never" and  "Never". It makes no difference. I walk away from the computer a few minutes and when I return, I return to a blank screen and I have to log back in before I can do anything. I just installed The 64 bit version the old 32 bit didn't do that.
Thanks,
Paul

---

### Post by Frogs Hair on 2012-08-10
You may want to check screen saver idle time also.

---

### Post by robtygart on 2012-08-10
I am having a problem that sounds like yours. 

I think this has something to do with DPMS


type 

```
xset -q
```

This is what I get ```
matt@matt-VGN~$ exset -q
No command 'exset' found, did you mean:
 Command 'xset' from package 'x11-xserver-utils' (main)
exset: command not found
matt@matt-VGN:~$ xset -q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    off    02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  250    repeat rate:  30
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  20/10    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 600    Suspend: 600    Off: 600
  DPMS is Enabled
  Monitor is On 

```

and if I type this 

```
xset -dpms
```

It will stay on and got go off, until I restart, and DPMS will be enabled again...


I hope this helps, and I get mine fixed too :P.

---

### Post by p3aul on 2012-08-10
Thanks! it was the screen saver

---

