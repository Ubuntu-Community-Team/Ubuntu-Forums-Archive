---
title: "ctrl key not working"
date: 2009-07-07
forum: General Help
---

### Post by adamgram on 2009-07-07
Hi.  I'm using Ubuntu 8.04 and my ctrl key does not work.  When I set it up there was not matching keyboard layout for my laptop keyboard so I just guessed and I think I guessed wrong.  Does anyone know of any database that matches keyboards by laptop brand to what is on the list in Ubuntu?  I'm using an old Gateway MA3 laptop.  No Gateways appear on my list under keyboard preferences.  Thanks!

---

### Post by synapsys on 2009-07-07
Did you try the default keyboard?

---

### Post by adamgram on 2009-07-07
yes.  the default is 'generic 105-key', but my laptop only has 86 keys

---

### Post by synapsys on 2009-07-07
Does the other ctrl key work?
Can you plug in an external keyboard and see if that ctrl key works?

---

### Post by adamgram on 2009-07-07
hey thank you for helping me with this

no, neither ctrl key works, and I plugged in the the keyboard from my desktop and neither ctrl keys work through it either.  it is a standard desktop keyboard made by dell and I count 104 keys.

---

### Post by adamgram on 2009-07-07
I also tried the external keyboard with it set to the 104 key keyboard and again neither ctrl key works

---

### Post by synapsys on 2009-07-07
Have you tried playing with the ctrl options?

System >> Preferences >> Keyboard
Layouts tab
Layout options button
Ctrl key position

---

### Post by adamgram on 2009-07-07
hmm... we may be on to something here!  if I switch either to 'make CapsLoc and additional Ctrl', 'swap Ctrl and CapsLock', or 'Ctrl key at left of'A'', the CapsLock key does work as a shift key.  I'd be happy with this as a workaround really because typing in all caps is a huge pet peeve of mine, but if that clues you in on the real fix, I'm all ears for that too.  thanks!

---

### Post by Keith_Beef on 2009-07-07
> **adamgram said:**
> hey thank you for helping me with this

no, neither ctrl key works, and I plugged in the the keyboard from my desktop and neither ctrl keys work through it either.  it is a standard desktop keyboard made by dell and I count 104 keys.

Well, if you leave the keymap without changes, and simply plug in a USB or PS/2 keyboard, I would not expect it to behave much differently around the shift, capslock, alt, control or meta keys...

What model of laptop is it, and is there a keymap proposed for it or for a similar layout?

K.

---

### Post by adamgram on 2009-07-07
> **Keith_Beef said:**
> 
What model of laptop is it, and is there a keymap proposed for it or for a similar layout?

K.

No sir.  It is a Gateway MA3 laptop (old) and there are no 'gateway' laptops on the list.  My initial thought was to find some sort of database listing other laptops that used the same keyboard configuration, in hopes of finding one of those on the list, but my internet search returned nill.

---

### Post by Keith_Beef on 2009-07-08
The only thing I can suggest, then, is to add the Keyboard Indicator applet to your Gnome panel. Right click on the applet, and select Show Current Layout.

Try also looking in that applet for Keyboard Preference - Layouts... there's one called Dell Laptop/notebook Prescision M series and another called Dell Precision M65.

If all else fails, you could write your own keymap.
Try reading these:
[http://www.linuxforums.org/forum/suse-linux-help/41302-special-keys-using-xmodmap.html](http://www.linuxforums.org/forum/suse-linux-help/41302-special-keys-using-xmodmap.html)
[http://www.linux.org/docs/ldp/howto/Intkeyb/x679.html](http://www.linux.org/docs/ldp/howto/Intkeyb/x679.html) 

Use Xev to find out what happens when you press the control keys. Below is the output when I press and release the left, then the right control keys on my Logitech keyboard.

```
KeyPress event, serial 33, synthetic NO, window 0x4a00001,
    root 0x13c, subw 0x0, time 12574393, (-524,545), root:(672,591),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4a00001,
    root 0x13c, subw 0x0, time 12574477, (-524,545), root:(672,591),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x4a00001,
    root 0x13c, subw 0x0, time 12575522, (-524,545), root:(672,591),
    state 0x10, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4a00001,
    root 0x13c, subw 0x0, time 12575624, (-524,545), root:(672,591),
    state 0x14, keycode 105 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

Good luck!

K.

---

### Post by tommcd on 2009-07-24
If you are still looking for a solution for the non-functioning ctrl key, see this thread:
[http://ubuntuforums.org/showthread.php?t=1210178](http://ubuntuforums.org/showthread.php?t=1210178)
That thread is for Ubuntu 9.04. This may work in 8.04 also, but I am not sure. It can't hurt to try it though.

---

