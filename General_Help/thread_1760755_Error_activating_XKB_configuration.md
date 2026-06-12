---
title: "Error activating XKB configuration"
date: 2011-05-17
forum: General Help
---

### Post by danmichael on 2011-05-17
Hi. 
I just installed Ubuntu 11.04 64bit on a MacBook (virtual installation using Parallels) and updated all packages. I have a Norwegian keyboard layout, and most of the keys actually works fine (even æ,ø,å), but I can´t type Alt-modified keys (for instance square brackets by Alt-8 and Alt-9). So I tried modifying the Alt-behaviour in the Keyboard pref panel, but upon saving I get

```
Error activating XKB configuration.
It can happen under various circumstances:
 &#8226; a bug in libxklavier library
 &#8226; a bug in X server (xkbcomp, xmodmap utilities)
 &#8226; X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
11001000

If you report this situation as a bug, please include:

``` &#8226; The result of xprop -root | grep XKB
```

_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "no", "mac_nodeadkeys", ""
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "no", "mac_nodeadkeys", ""

``` &#8226; The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

 model = macbook79
 options = [altwin    altwin:swap_lalt_lwin,lv3    lv3:alt_switch,grp    grp:shift_caps_toggle]
 layouts = [no    mac]

```Since I´m new to linux configuration, I´m not sure where to start looking for solutions.. Is there perhaps some xkb configuration files I should check for errors?

---

### Post by joel_ru on 2011-07-06
Hi All,

I had the same problem, as danmichael. I'm running Ubuntu Netbook Remix 10.10 (Maverick Meerkat) on laptop ASUS Eee PC 900. This message started to appear right after login, after waking up from Suspended state and after each exit from 'gnome-keyboard-properties'.
The cause of this problem is my alterations in 'gnome-keyboard-properties'.
I've changed on tab 'Layout' the default 'Keyboard model' value (don't remember exactly, what it was) to value 'ASUS laptop' because I thought this value would be more appropriate for my 80-keys keyboard. But I get instead this annoying message. I've looked through some forums ang found no definite answer. Today I've pushed the button 'Reset to Defaults' on the same tab 'Layout' in 'gnome-keyboard-properties' and the problem have disappeared. Till now I've spotted no aftermaths.

During this problem I had such outputs.

The result of xprop -root | grep XKB
```

_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us,ru", ",", "grp:alt_shift_toggle,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us,ru", ",", "grp:alt_shift_toggle,grp_led:scroll"

```The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```

 layouts = []
 options = [grp    grp:alt_shift_toggle,grp_led    grp_led:scroll]
 model = asus_laptop

```Though this message started to appear if I want to assign a Compose key in 'Keyboard Layout Options' window activated through button 'Options ...' on the same tab 'Layout' in 'gnome-keyboard-properties'. I've tried to assign 'Left Win' or 'Right Alt' keys for Compose key, but this message appeared promptly. So I still can't make assignations for Compose key.

---

