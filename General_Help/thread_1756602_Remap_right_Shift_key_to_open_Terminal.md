---
title: "Remap right Shift key to open Terminal"
date: 2011-05-12
forum: General Help
---

### Post by Antimethod on 2011-05-12
I never use the right Shift key for actual typing so it would be great if i could remap it to open a terminal.
I know how to set Super_L to open a terminal, but not the right shift.
Can anybody help me?

---

### Post by Xgen on 2011-05-12
I presently use the right mouse wheel button to open gnome terminal and the left to bring up the shutdown menu, but with xbindkeys you should be able to map any button or key.

Try:

Install "xbindkeys" and "xautomation"
Create an ".xbindkeysrc" file in your home folder

Add the following:

#Terminal Menu
"gnome-terminal"
  Shift_R

Save and relogin. Hopefully that works...


Oops...forgot to add:

Create a startup program in your Startup Applications called...whatever...(Key Mapping?)

Add: "xbindkeys" (without quotes) as the command to start the program when logging in.

---

### Post by Antimethod on 2011-05-12
Did just that and it worked.
Thanks!

---

