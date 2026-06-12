---
title: "locked out my keyboard"
date: 2011-01-23
forum: General Help
---

### Post by idoitprone on 2011-01-23
I was watching shows on hulu, then suddenly my dog jumped on the keyboard.  A dialog showed up, but I was unable to see it and my dog hit entered. Now I am locked out my key board on Ubuntu 10.10. The problem still presist after reboot.  I can only use my keyboard to loggin. The Fn keys still work and mouse atleast. It might be problem with the profile, since the guest dont have this problem. So can I get some direction to edit the profile

---

### Post by ajgreeny on 2011-01-23
If the keyboard still works in recovery mode from grub menu, or even if you login as user then go to Ctrl+Alt+F1 for a cli, try removing the folder **/home/*username*/.gconf/desktop/gnome/peripherals/keyboard**.

If that is no help to you, I have no other ideas, unfortunately.

---

### Post by idoitprone on 2011-01-24
nothing changed, i cant really enter tty console when i loggin as my user, but when i enter guest loggin. I will go the annoying method of entering root in failsafe and creating a new user.

---

### Post by ajgreeny on 2011-01-24
> **idoitprone said:**
> nothing changed, i cant really enter tty console when i loggin as my user, but when i enter guest loggin. I will go the annoying method of entering root in failsafe and creating a new user.
You can try that if you want to, but you can remove that **/.gconf/desktop/gnome/peripherals/keyboard** folder I spoke of in recovery mode as well.

---

### Post by idoitprone on 2011-01-26
Try that, nothing happen. It my fault I wasnt really clear. Could of answered sooner, but lock out of the forums ubuntu's problem

---

