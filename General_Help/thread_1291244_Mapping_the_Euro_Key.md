---
title: "Mapping the Euro Key"
date: 2009-10-14
forum: General Help
---

### Post by pravin on 2009-10-14
I have installed 9.10 beta on the NC10. I would like to map the Euro key (Fn + F3) - which doesn't work in 9.10 - to insert the £ symbol into my open document.

Can someone give me pointers? Thank you

---

### Post by eric3_14159 on 2009-11-09
First, you have to find out what event is being recognized by the X Windows system when you type Fn + F3. The only way I know to find the keycode is to use the program "xev". Run it, and put your mouse in the black box in the window that opens. Type a few keys. Watch the enormous number of lines scroll by. Eventually, once you're used to it, look for the "keycode" of each key that is being pressed, and of the combinations that show up. Find the keycode of Fn+F3. Record it.

Then, open the file ~/.xmodmaprc in your favorite text editor, creating it if it doesn't exist, and at the bottom put "keycode [the keycode you recorded] = XK_EuroSign". Test it by running "xmodmap ~/.xmodmaprc" in a terminal, and then typing Fn+F3 should make the Euro symbol appear.

After this, if Fn+F3 isn't recognized on subsequent reboots, go to System -> Preferences -> Startup Applications and add "xmodmap ~/.xmodmaprc" as a new command to run.

Hope this helps!

---

