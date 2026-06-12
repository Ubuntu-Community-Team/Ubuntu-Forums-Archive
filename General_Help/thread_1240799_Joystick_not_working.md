---
title: "Joystick not working"
date: 2009-08-15
forum: General Help
---

### Post by Mi*6d@# on 2009-08-15
Just bought great USB joystick Genius MetalStrike FF but there is one problem: I can't get it working. After plugging in it is detected neither by the system nor by Jscalibrator. Need help...

---

### Post by Mi*6d@# on 2009-08-15
Can anybody help plz?

---

### Post by Mi*6d@# on 2009-10-02
Bumping the topic in hope somebody answers.

My joystick appears to be detected by Linux somehow but unrecognized as an input device.

---

### Post by jonobr on 2009-10-02
Im not sure if this will help you much,and this is just speculation on my part as I have not used a joystick on Ubuntu before but if you open a terminal window
and type in xev
and hit enter it will open the event tester.


It opens two windows, one is debug the other is the testing window

If you use any input device, like a keyboard and mouse,
it will show here.

If you press a key on the keyboard, it would in the debug window

Heres an example of the keypress on the letter s

> 

KeyPress event, serial 33, synthetic NO, window 0x3a00001,
    root 0x81, subw 0x0, time 84591383, (117,64), root:(122,137),
    state 0x0, keycode 39 (keysym 0x73, s), same_screen YES,
    XLookupString gives 1 bytes: (73) "s"
    XmbLookupString gives 1 bytes: (73) "s"
    XFilterEvent returns: False



Heres the event for a mouse wheel roll

> ButtonPress event, serial 33, synthetic NO, window 0x3a00001,
    root 0x81, subw 0x0, time 84586665, (117,64), root:(122,137),
    state 0x0, button 4, same_screen YES

ButtonRelease event, serial 33, synthetic NO, window 0x3a00001,
    root 0x81, subw 0x0, time 84586665, (117,64), root:(122,137),
    state 0x800, button 4, same_screen YES

You get the mouse wheel or normal mouse motion debug only when the
mouse pointer is over the event screen.

I am guessing that if you place your mouse over the event window and make some joystick movements, it may show in the debug.

Im thinking if nothing shows up, there is nothing to be processed and I would be looking more towards the driver or hardware, or if you do see debub its between the processing of those movements and the application your running.

---

### Post by Mi*6d@# on 2009-10-03
It seems that kernel does not register joystick movements (no debug messages about that in terminal). As I said Linux detects the device but doesn't recognize it as joystick. Just some unknown USB device.

---

### Post by jonobr on 2009-10-06
IM thinking your only way forward here may be to contact the vendor to see if they have any linux drivers.
Im guessing they will say no.

---

