---
title: "Boot..."
date: 2011-03-24
forum: General Help
---

### Post by Andrenap on 2011-03-24
OK, I recently installed Ubuntu in my PC, without uninstalling windows coz it`s not really mine, its my father`s. When he saw the boot (like a month later, he REALLY uses the PC...) he went crazy and instantly ordered me to "uninstall that thing". Of course i`m not stupid to do that after a month of seeing how  Ubuntu is... I want to know if/how can I make the pc start on windows auto, without prompting by showing the choose system screen, and when i open boot menu (i don`t remember, but i think its F-eight) i have both choices, so I can keep Linux without him knowing... or should i use VBox?

---

### Post by Krytarik on 2011-03-24
Sneaky! :P

Make sure that the option "GRUB_HIDDEN_TIMEOUT=0" is in your "/etc/default/grub" and not outcommented:
[https://help.ubuntu.com/community/Grub2#/etc/default/grub%20(file)]("https://help.ubuntu.com/community/Grub2#/etc/default/grub%20%28file%29")

And follow tweak #11, method 2 of this guide:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Greetings.

---

### Post by Andrenap on 2011-03-25
I tryed it and got two things. 
One = it didnt work, dunno why.
Two = that would make ubuntu run auto, i want window auto n' ubuntu when i open boot menu

EDIT: I sucesfuly used it, but got the #2 problem, as i thought
EDIT2 : solved problem #2 by myself. I got a completely invisible ubuntu boot now. If anyone wanna know how, just PM, i guess i might remember my steps... By the way, thx for the help Krytaryk, couldn't do it without ur tuto

---

### Post by Krytarik on 2011-03-25
Ah, I didn't thought of the "GRUB_DEFAULT" option, but you already found it.

Then please this thread as "solved".

---

