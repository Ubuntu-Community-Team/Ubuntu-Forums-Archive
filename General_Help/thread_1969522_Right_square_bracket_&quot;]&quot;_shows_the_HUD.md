---
title: "Right square bracket &quot;]&quot; shows the HUD"
date: 2012-04-30
forum: General Help
---

### Post by sparhawkthesecond on 2012-04-30
Hi, after upgrading to Ubuntu 12.04, typing the right square bracket "]" brings up the HUD. It writes the character, then the HUD will immediately pop up (similar to left Alt). I checked my keyboard shortcuts via System settings, but it's just got "Alt L" listed.

FWIW this occurs on my laptop keyboard as well as the external one. I checked out xev, but everything seems to be pretty consistent (I can post the output if it's helpful). I'm not sure what else to do. Any help would be appreciated. 

Cheers.

Dell XPS17 L702X

---

### Post by sparhawkthesecond on 2012-05-02
And this seems to have been fixed with a few reboots and/or a recent update.

---

### Post by sparhawkthesecond on 2012-05-02
Hmm.. so this bug is back. I guess the reboot fixed it temporarily, and something triggered it again.

FWIW it occurred first in Firefox both times, although I don't know if that's coincidental. Anyone else getting this bug? (andrewmicky, did you accidentally quote my post with a misclick?)

---

### Post by sparhawkthesecond on 2012-05-02
Bizarre...
```
$ xmodmap -pm
xmodmap:  up to 3 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        bracketright (0x23),  Alt_L (0x85),  Alt_L (0xcc)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x40),  Super_R (0x6c),  Super_L (0xce)
mod5        ISO_Level3_Shift (0x5c),  ISO_Level3_Shift (0x86),  Mode_switch (0xcb)

```

---

### Post by sparhawkthesecond on 2012-05-02
This is the contents of my .Xmodmap file. I've modified it for my Apple keyboard. Mod1 looks fine to me...

```
! Swap Alt and Cmd keys.
keycode 37 =    Control_L
keycode 133 =   Alt_L Meta_L
keycode 64 =    Super_L
keycode 108 =   Super_R
keycode 134 =   ISO_Level3_Shift Multi_key
keycode 105 =   Control_R       Multi_key
clear Shift
clear Lock
clear Control
clear Mod1
clear Mod2
clear Mod3
clear Mod4
clear Mod5
add    Shift   = Shift_L Shift_R
add    Lock    = Caps_Lock
add    Control = Control_L Control_R
add    Mod1    = Alt_L 0x007D
add    Mod2    = Num_Lock
add    Mod4    = Super_L Super_R
add    Mod5    = Mode_switch ISO_Level3_Shift ISO_Level3_Shift ISO_Level3_Shift

! Configure '=' key on numpad as '='.
keycode 0x7D =  equal

```

---

### Post by sparhawkthesecond on 2012-05-02
> **sparhawkthesecond said:**
> 
add    Mod1    = Alt_L 0x007D
So removing "0x007D" seems to have fixed it for me. Googling "0x007D" suggests that it's mapped to the "}" key, so I guess for some reason "]" does a similar thing. The reason why I had this mapping in the first place was because I followed the instructions on the Ubuntu [help page.]("https://help.ubuntu.com/community/AppleKeyboard#Ubuntu_8.10_.28Intrepid_Ibex.29_through_10.04_.28Lucid_Lynx.29") I guess that's a typo there. I partially modified the help page, but I'm not 100% what the motivation was for that code in the first place, so I left the original there too. Please modify again if you are more certain than I am.

---

