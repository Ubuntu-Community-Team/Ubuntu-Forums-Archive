---
title: "Several keys stopped working"
date: 2009-08-27
forum: General Help
---

### Post by Lacho on 2009-08-27
Hi,

I have a Compaq Presario V2000 using Jaunty, and last week several keys stopped working; the del, home, pg up, pg dn, end, and side arrows.

I already ran xorg and the keyboard setup in preferences, but nothing changed, several days ago they all came back fine, but then died again.

Any suggestions?

---

### Post by SuaSwe on 2009-08-27
What keyboard layout do you have set up (in Preferences -> Keyboard)?

---

### Post by Lacho on 2009-09-01
SuaSwe,

Sorry for the delay, was out of the country and could reply till today.

I have chosen the Generic 105-Key (intnl) PC with a USA layout, but this bug comes and goes, just two days ago, everything was working fine, and then silently, the keys die

---

### Post by P4man on 2009-09-01
have a look in system > keyboard > mouse keys

Make sure its not enabled.

There used to be a bug (at least I think its fixed now) that mouse keys would be enabled sometimes for unclear reasons, especially when using remote desktop.

---

### Post by Lacho on 2009-09-02
P4man,

Just checked, and no, it is not enabled.

Anybody else, any suggestions?

---

### Post by tgalati4 on 2009-09-02
Cut and paste the output of xev while pressing the bad keys.

For instance, when I press Down Arrow and Right Arrow I get:

KeyPress event, serial 32, synthetic NO, window 0x3c00001,
    root 0  x 84, subw 0x0, time 5667815, (108,148), root:  (770,175),
    state 0  x 0, keycode 116 (keysym 0xff54, Down  ), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0 x 84, subw 0x0, time 5667974, (108,148), root:  (770,175),
    state  0 x 0, keycode 116 (keysym 0xff54, Down  ), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


KeyPress event, serial 35, synthetic NO, window 0x3c00001,
    root 0x  84, subw 0x0, time 5671634, (108,148), root:  (770,175),
    state 0x  0, keycode 114 (keysym 0xff53, Right  ), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x3c00001,
    root 0x  84, subw 0x0, time 5671769, (108,148), root:(770,175),
    state 0x  0, keycode 114 (keysym 0xff53, Right  ), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


You should get 2 entries for each keypress (one for press, one for release).  There should be a valid key symbol (keysym) with an appropriate name and a valid keycode that is associated with it.

Ignore the random smilies.

---

### Post by QIII on 2009-09-02
Simple hardware check?

Try external keyboard?

---

### Post by QIII on 2009-09-02
Dang smiles...

They seem to be caused by colon/open paren and open/close paren emoticon combinations...

:)   :(   :)

---

### Post by Lacho on 2009-09-03
Tried XEV, and other keys do register, but the useless ones do not, is this like THE definitive test that the keys (hardware) are not working, or could it still be something software related (Ubuntu)?

---

### Post by unutbu on 2009-09-03
I'm reluctant to call any of the following "definitive", but you could test if the problem keys work in these situations:
[list]
[*] Press Ctrl-Alt-F1 this will take you to a text terminal. xev relies on a working X server. The text terminal does not rely on an X server, so you are a little closer to hardware here. 
[*] While booted from a LiveCD (Ubuntu or otherwise) and see if the keys work there
[*] Install Windows into a partition -- am I really writing this? -- and see if the keys work there
[/list]

If the problem persists in all these situations, then I think it is likely it is hardware failure. If the problem keys work in any of these situations, then obviously it is a software problem.

---

### Post by P4man on 2009-09-03
you could try the bios? If the arrow keys work there, then it may not be a hardware issue. If they don't, you can be certain.

Actually, if they don't work in grub, you can pretty sure its a hardware issue. Im not sure what you mean by "side arrows", but if its left/right, they dont do anything in grub (I think), but ANY key should stop the countdown (if you have set one in the menu).

---

### Post by unutbu on 2009-09-03
P4man, that is a good idea. Moreover, if you get to the GRUB menu and press 'e' to edit the boot command, then the left/right arrow keys should move the cursor around. 
The up/down arrows should allow you to select various lines in the GRUB menu.
So indeed, that would be a pretty low-level test of whether or not the arrow keys work.

---

### Post by Lacho on 2009-09-07
Thanks for the ideas, since at the moment the keys are all working, I cannot try them, but (hopefully not) as soon as they fail I will post my results.

---

