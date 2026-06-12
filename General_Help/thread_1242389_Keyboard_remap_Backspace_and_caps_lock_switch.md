---
title: "Keyboard remap: Backspace and caps lock switch"
date: 2009-08-17
forum: General Help
---

### Post by oscurochu on 2009-08-17
I am trying to switch my caps lock and back space keys. I use the caps lock key occasionally and so cant just "remove" it. When I press on the caps lock key, or the new back space key, caps lock is turned on (or off). When I press the actual backspace key, the new caps lock key, nothing happens.

This is what I've done:

```
xmodmap -e 'keycode 66=BackSpace'
xmodmap -e 'keycode 22=Caps_Lock'
```Output of xev when caps lock, the new back space, is pressed:
```
PropertyNotify event, serial 30, synthetic NO, window 0x4c00001,
    atom 0x127 (XKLAVIER_STATE), time 38914435, state PropertyNewValue

KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 38914524, (591,681), root:(596,730),
    state 0x12, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False
```Out put of xev when back space, the new caps lock, is pressed:
```
KeyPress event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 39027980, (419,98), root:(424,147),
    state 0x10, keycode 22 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 39028084, (435,128), root:(440,177),
    state 0x10, keycode 22 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```Using Ubuntu 9.04, if that matters. :)

---

### Post by Lostin60's on 2009-09-02
> **oscurochu said:**
> I am trying to switch my caps lock and back space keys. I use the caps lock key occasionally and so cant just "remove" it. When I press on the caps lock key, or the new back space key, caps lock is turned on (or off). When I press the actual backspace key, the new caps lock key, nothing happens.

This is what I've done:

```
xmodmap -e 'keycode 66=BackSpace'
xmodmap -e 'keycode 22=Caps_Lock'
```Output of xev when caps lock, the new back space, is pressed:
```
PropertyNotify event, serial 30, synthetic NO, window 0x4c00001,
    atom 0x127 (XKLAVIER_STATE), time 38914435, state PropertyNewValue

KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 38914524, (591,681), root:(596,730),
    state 0x12, keycode 66 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False
```Out put of xev when back space, the new caps lock, is pressed:
```
KeyPress event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 39027980, (419,98), root:(424,147),
    state 0x10, keycode 22 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 39028084, (435,128), root:(440,177),
    state 0x10, keycode 22 (keysym 0xffe5, Caps_Lock), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```Using Ubuntu 9.04, if that matters. :)

You have to "remove" Caps_Lock from the modifier table to make your changes.  You can then add it back. And you can set, for instance Keycode = symbol symbol symbol symbol. Where the first symbol is the unmodified action of the key, and the 2nd is "shift + key" There is an almost identical example in the manual.

---

