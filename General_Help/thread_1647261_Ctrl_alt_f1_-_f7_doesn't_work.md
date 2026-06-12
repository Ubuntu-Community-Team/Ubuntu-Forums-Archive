---
title: "Ctrl alt f1 - f7 doesn't work"
date: 2010-12-17
forum: General Help
---

### Post by Parapan on 2010-12-17
Hello all,

I tried search for a solution for this from google but couldn't find much that would help me. I just installed a fresh copy of Ubuntu 10.04 from the live cd, and now I want to install the nvidia drivers. But i'm not able to access the terminal. Ctrl + alt + f1-f7 does nothing. 

Also, doing sudo service gdm stop, puts me in the black screen where it gets stuck at 
"Checking Battery state", with a blinking cursor following it. I can type stuff but it doesn't do anything. No terminal, no response.

After that the only thing that works is alt+ctrl+delete , which shows me the ubuntu logo for a few seconds , with a few lines in the black screen before the restart happens.

Sorry i'm really new to linux so I'm not sure what files or configs I can show you guys to help with this unless you ask for something specifically..

Thanks in advance!

---

### Post by Parapan on 2010-12-18
Wow. My cousin just walked in casually asked me if it had something to do with F-Lock button on my keyboard (Microsoft Wireless Comfort 4000). And he was right. For those of you using the Microsoft Wireless desktop 4000, or similar keyboards with the F-Lock key (Toggles f1-f12 buttons bettween regular usage and custom usage), note that, THE KEYBOARD F-LOCK KEY FUNCTION IS REVERSED IN UBUNTU. Normally on windows you need to keep it off to use f1-f12. But in Ubuntu it needs to be on to use f1-f12. Hope this saves people a lot of time.

---

### Post by Krytarik on 2010-12-18
I've a Logitech Internet Navigator keyboard and it also has that F-key-switch. After boot the indicating LED -which reads "F"- is off, to activate the F-keys I have to press it, then the LED is on, thus it's the expected behaviour in Ubuntu, although annoying because I only use the F-key-function, not the special functions they offer alternatively.

Greetings

---

### Post by 1-L on 2011-03-23
If you get tired of having to press the F-Lock key on your Microsoft keyboard every time you start your computer, you can do the following fix. As root, edit the file /etc/rc.local and add the following lines:
setkeycodes bb 59 # Help  -> F1
setkeycodes 88 60 # Undo  -> F2
setkeycodes 87 61 # Redo  -> F3
setkeycodes be 62 # New   -> F4
setkeycodes bf 63 # Open  -> F5
setkeycodes c0 64 # Close -> F6
setkeycodes c1 65 # Reply -> F7
setkeycodes c2 66 # Fwd   -> F8
setkeycodes c3 67 # Send  -> F9
setkeycodes a3 68 # Spell -> F10
setkeycodes d7 69 # Save  -> F11
setkeycodes d8 70 # Print -> F12
Next time you boot you can forget about the F-Lock key.

---

