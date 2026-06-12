---
title: "Ctrl-key working as Alt-key, but not the the other way...."
date: 2010-02-18
forum: General Help
---

### Post by Osamabingandhi on 2010-02-18
Really strange problem i've got. I like to use the ctrl-key and then mark files with a mouse click. Now it is not working anymore. Instead when i press ctrl it takes a hold of the window it is currently over if i click and drag.

I don't know what to search for so i hope someone knows a solution

cheers
/Jakob
ubuntu 9.10

---

### Post by pi/roman on 2010-02-18
Here's what you can do to try to diagnose the problem by running:
```
xev | grep keycode
```And then press your control and alt keys. You can get more diagnostics without the grep but it reduces a lot of junk.  Here's my output for an example where left control is keycode 37 and left alt is keycode 64:
>     state 0x0, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,So then you can check your keycodes:
```
xmodmap -pke | grep '64\|37'
```and you'll get some extra junk but just ignore it.
Here is my output:
> keycode  37 = Control_L NoSymbol Control_L NoSymbol Control_L
keycode  64 = Alt_L Meta_L Alt_L Meta_L Alt_L Meta_LAnd then you should check the modifier keys:
```
xmodmap -pm
```Here are my ctrl and alt modifiers:
> control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Alt_R (0x6c),  Meta_L (0xcd)I don't know if you've noticed any inconsistencies yet, but if so then you've identified the problem.

---

### Post by Osamabingandhi on 2010-02-19
Hmm, the first try looks ok, but the second command looks strange:

xmodmap -pm
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

This looks like the problem, the numpad doesn't work either. The mod lines i guess is the problem. Do you know how to change these values?

---

### Post by skarychinezeguie on 2010-02-19
call me crazy, but did you accidentally set up something in compiz that uses the ctrl key? I use my ctrl and numberpad keys for snapping my windows to different sections of the screen but i can still use ctrl to select icons as well. idk. just a thought. have you made any recent changes? or is this an all-of-the sudden problem?

---

### Post by pi/roman on 2010-02-19
I think guie might be onto it. The output shows it's missing an altR modifier but that's no big deal. You could try checking window properties other than compiz if you have that, alt/f2: type "gnome-window-properties" and check out the settings there.

---

### Post by Osamabingandhi on 2010-02-20
This problem is quite sudden, cannot remember me doing something to change the keyboard settings.

I'll look into the gnome-settings and go over compiz.

---

### Post by Osamabingandhi on 2010-02-20
Ok the gnome-window settings were set to ctrl to move windows around witch explains a lot ;-P

But my numlock keys still don't work for some reason...

Any idea anyone?

---

### Post by pi/roman on 2010-02-21
Here is the output for my number lock.
```
xmodmap -pke | grep keycode
```
>     state 0x0, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,
    state 0x10, keycode 77 (keysym 0xff7f, Num_Lock), same_screen YES,

```
xmodmap -pke | grep 77
```
> keycode  77 = Num_Lock Pointer_EnableKeys Num_Lock Pointer_EnableKeys Num_Lock Pointer_EnableKeys

How is your num lock misbehaving?

---

### Post by Osamabingandhi on 2010-02-22
got this from: xmodmap -pke | grep 77

keycode  77 = Num_Lock Pointer_EnableKeys Num_Lock Pointer_EnableKeys Num_Lock Pointer_EnableKeys
keycode 177 = XF86Phone NoSymbol XF86Phone NoSymbol XF86Phone

the other command gave me around 100lines

---

### Post by pi/roman on 2010-02-22
> **Osamabingandhi said:**
> the other command gave me around 100lines
I flubbed that command but it doesn't matter, your keymap looks good and your modifier settings look good too.

What exactly is your number lock doing or not doing and when does it occur, perpetually or after pressing a key?

---

