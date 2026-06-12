---
title: "keyboard layout"
date: 2010-01-26
forum: General Help
---

### Post by icobra on 2010-01-26
Hi.

Initial state of installed Xubuntu 9.10 was ok - 2 layouts (us,ru) and a scroll led turns on while in alternative (ru) layout. 

After some actions (like opening xfce4-keyboard-settings and xfce4-xkb-plugin) layouts were eventually reset to default (us only). I added ru layout using these apps so all was ok except the scroll led.

Problem is that I can't get this led shining while in alt layout again. I tried following:

1. /etc/X11/xorg.conf now contains:
```
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "hp6000"
	Option      "XkbLayout" "us,ru"
	Option      "XkbOptions" "grp:alt_shift_toggle,grp_led:scroll"
```
Did nothing.

2. /etc/default/console-setup now contains:
```
XKBMODEL="hp6000"
XKBLAYOUT="us,ru"
XKBVARIANT=","
XKBOPTIONS="grp:alt_shift_toggle,grp_led:scroll"
```
Still no result.

3. After running
```
setxkbmap -layout "us,ru" -option "grp:alt_shift_toggle,grp_led:scroll"
```
works as needed but after opening xfce4-xkb-plugin->Parameters gets broken again (seems like plugin is using some another cfg info but where it is?)

Please tell me where to check more to fix this problem or where I can get more info about it. Thanks.

---

