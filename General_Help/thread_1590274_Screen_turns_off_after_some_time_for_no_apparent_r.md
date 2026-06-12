---
title: "Screen turns off after some time for no apparent reason"
date: 2010-10-07
forum: General Help
---

### Post by HeartAttack on 2010-10-07
Pretty much what the title says. It's really annoying. Neither the screensaver nor... energy saving (or whatever it's called in English...) are enabled, yet the screen turns off after, like, ten minutes without interaction as if a screensaver were enabled.

This first occured after the last kernel update (though it might as well have been some other update installed at the same time, I don't know) and I both googled and used the forum search - in vain, since no search result showed the same problem, just black screens on startup or while using the system.

Oh, by the way: Lucid.

---

### Post by Boring on 2010-10-07
Have you tried going to **System** -> **Preferences** -> **Power Management**?

---

### Post by HeartAttack on 2010-10-07
Ah, Power Management it was. Yes, I did and it's on "never".

---

### Post by Boring on 2010-10-07
What type of graphics card are you using?

---

### Post by HeartAttack on 2010-10-07
That'd be an nVidia GeForce 8600GT, for which I am using the proprietary drivers.

---

### Post by Boring on 2010-10-07
I have an ATI graphics card, so you may not have the same options as me, but I have extra functions that I am able to set by going to
**System** -> **Preferences** -> **ATI Catalyst Control Center** (For me).

---

### Post by HeartAttack on 2010-10-07
Well, yeah, there's "NVIDIA X Server Settings", which doesn't have any such option as I am looking for.

---

### Post by sisco311 on 2010-10-07
Open a terminal and post the output of:
```
cat /etc/X11/xorg.conf
```
and
```
xset q
```

---

### Post by Quackers on 2010-10-07
Is this on a laptop or a desktop?

---

### Post by HeartAttack on 2010-10-08
> **sisco311 said:**
> Open a terminal and post the output of:
```
cat /etc/X11/xorg.conf
```and
```
xset q
```
Alright:
cat /etc/X11/xorg.conf:
> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection


xset q:
> Keyboard Control:
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
  bell percent:  50    bell pitch:  400    bell duration:  100
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

---

### Post by Ambidextrous on 2010-10-12
I had the same problem using 10.04.  I was hoping the upgrade to 10.10 would fix it.

But no! 

I'm also using Nvidia-based cards (2 GeForce 9500 GT's) and I can't find anything in the Nvidia X-Server settings which might change this behavior.

---

