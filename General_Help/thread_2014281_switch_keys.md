---
title: "switch keys"
date: 2012-07-01
forum: General Help
---

### Post by chapra on 2012-07-01
Hi, I just got a new laptop, and it's a Dell.  Unfortunately, the Dell manufacturers switched the positions of the right control key and the menu key, which is very aggravating.  I've seen instructions online for switching modifier keys, but not the menu key.  Is there a way to switch the keys?

Thanks

---

### Post by matt_symes on 2012-07-01
Hi

> **chapra said:**
> Hi, I just got a new laptop, and it's a Dell.  Unfortunately, the Dell manufacturers switched the positions of the right control key and the menu key, which is very aggravating.  I've seen instructions online for switching modifier keys, but not the menu key.  Is there a way to switch the keys?

Thanks

You need to use the xmodmap command to switch the keys.

To do this you need to find the key codes for those keys on your system. You can do this using the command

```
xev
```Open a terminal and type

```
xev
```This will open a small window. Whenever you move your mouse over that window or press any key you will get some output in the main terminal window.

Press the menu key. You will see output similar to this...

```
KeyPress event, serial 32, synthetic NO, window 0x2600001,
    root 0x161, subw 0x0, time 9862168, (419,51), root:(420,142),
    state 0x0, **keycode 135** (keysym 0x38, 8), same_screen YES,
    XKeysymToKeycode returns keycode: 17
    XLookupString gives 1 bytes: (38) "8"
    XmbLookupString gives 1 bytes: (38) "8"
    XFilterEvent returns: False
```Make a note of the keycode. You want to do the same with the Right Ctrl Key.
```

KeyPress event, serial 32, synthetic NO, window 0x2600001,
    root 0x161, subw 0x0, time 10046862, (264,396), root:(265,487),
    state 0x0, **keycode 105** (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: Fals
```Mine is 135 for the menu key and 105 for the Right Ctrl key.

You can then swap them around by typing into the terminal. This would be mine.

```
xmodmap -e "keycode 135 = 105"
```Test it out. This will not persist between reboots.

To make it persist create the file 

```
~/.xmodmap
```and add the xmodmap command (like mine above) you used to test.

Any problems then post back here.

Kind regards

---

### Post by chapra on 2012-07-02
Hi Matt_Syms,

Thanks for the reply. The solution partly works.  I was able to map the menu key funtion to the control key by entering in 
xmodmap -e "keycode 105 = Menu", 

however, the reverse did not work.  

xmodmap -e "keycode 135 = Control_R" simply disables the menu key.  

Your suggestion, to enter "keycode 135 =105" mapped one of the keys to the letter "i" and had no effect on the other.  I've been playing around with the format I entered, of mapping a code to the title of another key, and it seems to be selective in how it works.  Assigning the function of either control key or either alt key to other keys seems to be where the trouble is.  

Also, I tried switching caps lock and numlock.  The effect was that the numlock was disabled entirely, and the capslock now turns on both capslock and numlock.

chapra

---

### Post by matt_symes on 2012-07-02
Hi

> Your suggestion, to enter "keycode 135 =105" mapped one of the keys to the letter "i" and had no effect on the otherMy suggestion wasn't for you to enter my keycodes verbatim. Don't use my key codes if yours are different.

You need to make sure you are using your keymap. Mine may be different than yours.

Did you find your key codes using xev ?

Post back the output from xev after pressing the relevent keys and we can check for you.

EDIT: Please bear in mind i have a UK keyboard.

Kind regards

---

### Post by chapra on 2012-07-06
> **matt_symes said:**
> Hi

My suggestion wasn't for you to enter my keycodes verbatim. Don't use my key codes if yours are different.

You need to make sure you are using your keymap. Mine may be different than yours.

Did you find your key codes using xev ?

Post back the output from xev after pressing the relevent keys and we can check for you.

EDIT: Please bear in mind i have a UK keyboard.

Kind regards


No, I actually had the same numbers for the right control and menu as you did.  I posted the exact code that I entered.  I ues xev to find mine just like you did.  Here's the output when pressing the right control key: 

KeyRelease event, serial 33, synthetic NO, window 0x3e00001,
    root 0x101, subw 0x0, time 339633, (266,95), root:(267,174),
    state 0x14, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

The following is for the menu key:

KeyPress event, serial 33, synthetic NO, window 0x3e00001,
    root 0x101, subw 0x0, time 406399, (250,410), root:(251,489),
    state 0x10, keycode 135 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x3e00001,
    root 0x101, subw 0x0, time 406526, (250,410), root:(251,489),
    state 0x10, keycode 135 (keysym 0xff67, Menu), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

It gives a message upon pressing and releasing.

xmodmap -e "keycode 135 = 105"  This command turns the menu key into the key for the letter i, or I  if the shoft or capslock is on.  The reverse has no effect.

chapra

---

### Post by chapra on 2012-07-11
Hi again,

I did find a solution.  I got it to work, but I need to make it permanent.  I'm not sure I understand your instructions on how to create an ./xmodmap file.  

The problem was that, because the control key is a special modifier key, I needed to add the third command:

xmodmap -e "keycode 135 = Control_R"

xmodmap -e "keycode 105 = Menu"

xmodmap -e "add Control = Control_R"

This, however, is erased upon reboot so I have to keep entering it in every time.

Chapra

---

