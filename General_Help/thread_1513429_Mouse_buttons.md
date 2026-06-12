---
title: "Mouse buttons"
date: 2010-06-19
forum: General Help
---

### Post by mithran on 2010-06-19
hey, i simply want to make it so that when i click the middle mouse button or the extra buttons (other that the standard left and right) it presses the super button.

in windows this is very easy and the settings are strait forward but i see no such option in the ubuntu mouse preferences, please help

i just want to press the super button with out having to use the keyboard, and it would be great if i could use my other gaming mouse buttons as well.

im dual booting win7 and ubuntu 10.04

---

### Post by jesuisbenjamin on 2010-06-19
Hi there,

I am not 100% sure of my answer but the filter-mouse may be what you are looking for, see the man pages.
You have to edit make a text file and assign buttons to keys (although the example is showing key to button, perhaps you the opposite is true as well). Hope this helps.

B.

---

### Post by mithran on 2010-06-19
Uuhhh, im not that linux pro...could i get a more step by step how to? thanks

---

### Post by jesuisbenjamin on 2010-06-20
Ok,

as i said i am not familiar with this, but here is what i think can be done.
The program filter-mouse can be run to convert mouse-events to key-strokes.
This program needs a text-file where the mouse-key correspondences are defined. Examples are given in the documentation of filter-mouse: [http://linux.die.net/man/7/filter-mouse](http://linux.die.net/man/7/filter-mouse)

No i suspect the file could contain:
```
#BUT buttonnumber TO KEY modmask modvalue button label  symbol 
BUT 2 TO KEY  0x0004  0x0004   0xffff 0x000d 0xffff   # Super

```

The problem is i have no idea what "modmask", "modvalue", "button" and "label" stand for. I reckon they must be specific to the key-stroke you want to simulate with your mouse.
Second i don't know if filter-mouse can handle mouse-to-key events (not stated in documentation)

So i hope someone more qualified can help further with this.

This is the best i have.
B.

---

### Post by mithran on 2010-06-20
thanks for getting back to me... im already using a program called easy strokes to use gestures for keystrokes. what i really need is to be able to access my mouse's button settings, the mouse preferences pages doesn't give any button customization options...

---

