---
title: "xmodmap error - help?"
date: 2010-08-11
forum: General Help
---

### Post by dewdrop_world on 2010-08-11
I hope this will be a quick question. On my netbook, I was able to use xmodmap to switch the modifiers into the order that I want. I just installed 10.04 on a new laptop (MSI A6200) and xmodmap is throwing an error I'm not clear how to interpret.

I confirmed with xev the names of the default modifier mappings -- from left to right,

```
Control_L    Super_L    Alt_L    <space>    ISO_Shift_3    Menu    Control_R
```

Instead, I want

```
Super_L    Alt_L    Control_L    <space>    Control_R    Alt_L*    Menu
```

* For the moment, I'm not concerned about the difference between ALT and ISO_Shift_3 -- I just want the second key to the right of the space bar to behave like Alt.

I copied the script that worked on the netbook and changed Alt_R to ISO_Shift_3 -- here's the script I'm running on the new machine.

```
remove control = Control_L Control_R
remove mod1 = Alt_L ISO_Shift_3 Meta_L
remove mod4 = Super_L
keysym Control_L = Super_L
keysym Control_R = Menu
keysym Super_L = Alt_L
keysym Menu = ISO_Shift_3
keysym Alt_L = Control_L
keysym ISO_Shift_3 = Control_R
add mod1 = Alt_L ISO_Shift_3 Meta_L
add control = Control_L Control_R
add mod4 = Super_L
```

Verbose output from xmodmap:

```
dlm@dlm-laptop:~$ xmodmap -verbose Documents/xmm-try.txt
! Documents/xmm-try.txt:
! 1:  remove control = Control_L Control_R
! Keysym Control_L (0xffe3) corresponds to keycode(s) 0x25
! Keysym Control_R (0xffe4) corresponds to keycode(s) 0x69
        remove control =  0x25 0x69
! 2:  remove mod1 = Alt_L ISO_Level3_Shift Meta_L
! Keysym Alt_L (0xffe9) corresponds to keycode(s) 0x40 0xcc
! Keysym ISO_Level3_Shift (0xfe03) corresponds to keycode(s) 0x5c 0x6c
! Keysym Meta_L (0xffe7) corresponds to keycode(s) 0xcd
        remove mod1 =  0x40 0xcc 0x5c 0x6c 0xcd
! 3:  remove mod4 = Super_L
! Keysym Super_L (0xffeb) corresponds to keycode(s) 0x85 0xce
        remove mod4 =  0x85 0xce
! 4:  keysym Control_L = Super_L
! Keysym Control_L (0xffe3) corresponds to keycode(s) 0x25
        keycode 0x25 = Super_L
! 5:  keysym Control_R = Menu
! Keysym Control_R (0xffe4) corresponds to keycode(s) 0x69
        keycode 0x69 = Menu
! 6:  keysym Super_L = Alt_L
! Keysym Super_L (0xffeb) corresponds to keycode(s) 0x85 0xce
        keycode 0xce = Alt_L
        keycode 0x85 = Alt_L
! 7:  keysym Menu = ISO_Level3_Shift
! Keysym Menu (0xff67) corresponds to keycode(s) 0x87
        keycode 0x87 = ISO_Level3_Shift
! 9:  keysym Alt_L = Control_L
! Keysym Alt_L (0xffe9) corresponds to keycode(s) 0x40 0xcc
        keycode 0xcc = Control_L
        keycode 0x40 = Control_L
! 10:  keysym ISO_Level3_Shift = Control_R
! Keysym ISO_Level3_Shift (0xfe03) corresponds to keycode(s) 0x5c 0x6c
        keycode 0x6c = Control_R
        keycode 0x5c = Control_R
! 11:  add mod1 = Alt_L ISO_Level3_Shift Meta_L
        add mod1 = Alt_L ISO_Level3_Shift Meta_L
! 12:  add control = Control_L Control_R
        add control = Control_L Control_R
! 13:  add mod4 = Super_L
        add mod4 = Super_L
!
! executing work queue
!
        remove control =  0x25 0x69
        remove mod1 =  0x40 0xcc 0x5c 0x6c 0xcd
        remove mod4 =  0x85 0xce
        keycode 0x25 = Super_L
        keycode 0x69 = Menu
        keycode 0xce = Alt_L
        keycode 0x85 = Alt_L
        keycode 0x87 = ISO_Level3_Shift
        keycode 0xcc = Control_L
        keycode 0x40 = Control_L
        keycode 0x6c = Control_R
        keycode 0x5c = Control_R
        add mod1 = Alt_L ISO_Level3_Shift Meta_L
        add control = Control_L Control_R
        add mod4 = Super_L
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  118 (X_SetModifierMapping)
  Value in failed request:  0x17
  Serial number of failed request:  22
  Current serial number in output stream:  22
```

How should I change the script to work properly?

Thanks --
James

---

### Post by dewdrop_world on 2010-08-12
Well, I found a tutorial this morning - [http://www.in-ulm.de/~mascheck/X11/xmodmap.html](http://www.in-ulm.de/~mascheck/X11/xmodmap.html) - and rewrote the script like this, and it works now. I'd hoped to avoid using keycodes but for this, "working" is better than "elegant." The tutorial explains where to find the keycodes.

```
!note: This disables iso_level3_shift/mode_switch, maybe fix later
clear Control
clear Mod1
clear Mod4
clear Mod5
keycode  37 = Super_L
keycode 133 = Alt_L
keycode  64 = Control_L
keycode 108 = Control_R
keycode 135 = Alt_R
keycode 105 = Menu
add control = Control_L Control_R
add mod1    = Alt_L Alt_R
add mod4    = Super_L
```

James

---

