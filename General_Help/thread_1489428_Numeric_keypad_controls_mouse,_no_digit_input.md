---
title: "Numeric keypad controls mouse, no digit input"
date: 2010-05-21
forum: General Help
---

### Post by aeternitas on 2010-05-21
I've noticed a bit of a problem here in the last few days...after some point, my numeric keypad stops being a numeric keypad; instead, it controls the mouse (5 right clicks, and the outer keys move the cursor in the appropriate direction).  It doesn't appear to happen on boot, as I generally type the numeric bits of my password with the keypad, but some point after.  The only common events I can think of where this has occurred is either after connecting to the system via SSH, or after swapping to tty1 (which usually requires re-enabling of numberlock for the terminal to recognize digits, again for the password).  No matter what state the NumLock is in (off or on) at this point, the keypad fails to function as a keypad.  Ideas?

---

### Post by aeternitas on 2010-05-21
Nevermind, think I found my solution; disabling 'Allow keypad to control the mouse' in System -> Preferences -> Assistive Technologies -> Keyboard Accessibility -> Mouse Keys seems to have eliminated this behaviour, though it is a bit odd that it doesn't go that way from the outset.

---

### Post by JonHale on 2010-09-10
I had the same problem with almost the same solution on Lucid.
The only difference was that the control was located at
System->Preferences->Keyboard on the "Mouse Keys" tab.

---

