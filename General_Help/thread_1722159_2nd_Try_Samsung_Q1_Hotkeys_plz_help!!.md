---
title: "2nd Try: Samsung Q1 Hotkeys plz help!!"
date: 2011-04-05
forum: General Help
---

### Post by Paco009 on 2011-04-05
I recently put Ubuntu (10.10) on my Samsung Q1-U and have everything up and running except for the built-in hotkey controls.

The buttons which under windows handle page up/down and browser forward/backwards are unresponsive under Ubuntu.

After a little digging it seems that Ubuntu sees these keys as F1 through F4 when pressed, but I cannot make these keys act in the desired way (page up/down, forward/backwards)

Basically I need a script or something of the sort to make F1 page up, F2 forwards, F3 page down, and so on...

Compiz advanced has a built in tool to execute scripts wen a key combo is pressed, but I don't know the actual script necessary to scroll down or any of the other desired actions.

Any help would really be appreciated,
Thanks!!

---

### Post by Paco009 on 2011-04-05
I recently put Ubuntu (10.10) on my Samsung Q1-U and have everything up and running except for the built-in hotkey controls.

The buttons which under windows handle page up/down and browser forward/backwards are unresponsive under Ubuntu.

After a little digging it seems that Ubuntu sees these keys as F1 through F4 when pressed, but I cannot make these keys act in the desired way (page up/down, forward/backwards)

Basically I need a script or something of the sort to make F1 page up, F2 forwards, F3 page down, and so on...

Compiz advanced has a built in tool to execute scripts wen a key combo is pressed, but I don't know the actual script necessary to scroll down or any of the other desired actions.

Any help would really be appreciated,
Thanks!!

---

### Post by Paco009 on 2011-04-05
I recently put Ubuntu (10.10) on my Samsung Q1-U and have everything up and running except for the built-in hotkey controls.

The buttons which under windows handle page up/down and browser forward/backwards are unresponsive under Ubuntu.

After a little digging it seems that Ubuntu sees these keys as F1 through F4 when pressed, but I cannot make these keys act in the desired way (page up/down, forward/backwards)

Basically I need a script or something of the sort to make F1 page up, F2 forwards, F3 page down, and so on...

Compiz advanced has a built in tool to execute scripts wen a key combo is pressed, but I don't know the actual script necessary to scroll down or any of the other desired actions.

Any help would really be appreciated,
Thanks!!

---

### Post by uRock on 2011-04-05
Triplicate threads merged.

---

### Post by Krytarik on 2011-04-05
You can remap the buttons by simply creating a file called ".Xmodmap" in your home directory with the following content:

~/.Xmodmap:```

keysym F1 = Prior
keysym F2 = XF86Forward
keysym F3 = Next
keysym F4 = XF86Back
```The next time you login, you will most probably be asked if you want to use those keymap file*, then just choose "Add" and confirm with "OK". It should work then.

Greetings.

*depends on if you had such a file before, and did already confirm/disable those query

---

### Post by schievelbein on 2011-04-14
I am getting ready to try and install on my old NP-Q1 also.
Is there any advise, checklist, links that you can point me to to shorten my frustration time?

THANKS

---

### Post by tenach on 2012-02-06
Putting 11.10 on my household SQ1! So far everything is working flawlessly, thanks to the keysym suggestion. :D

---

