---
title: "Keyboard freeze"
date: 2011-10-22
forum: General Help
---

### Post by Gillingham on 2011-10-22
Hi

I have just upgraded to 11.10 and have encountered a small problem. The keyboard does not respond when I press a key.  After this the keyboard is frozen.  The mouse works so I have some access using the onscreen keyboard.

If I use control alt F1 before I log in using lightDM I can get access to a terminal and the keyboard works, also after rebooting the keyboard also works until I try to log in.  So I am confident that this isn't a hardware fault.

Any suggestions?

David

---

### Post by zero2xiii on 2011-10-22
Hay,

Is this a usb or a ps/2 kb? Have you tried plugin it out and back in.

If the problem presist, please supply the output of:

sudo lsusb #if it is a usb kb
sudo lspci #if it is a ps/2 kb i think this will list it, not sure.

Maybe there is an issue with the keyboard settings as such? Check when you log in what is the kayboard prefference set at, at the bottom of the screen.

Cherz

---

### Post by Gillingham on 2011-10-22
Hi

Thank you for your help

It is a PS2 keyboard which doesn't show up on lspci.

I have tried unplugin and plugin in the keyboard, but as it is a PS2 keyboard that had no effect.

What is good news however, is that I created a new user and the keyboard does work.  So I either need to move over to the new user or workout which config file I need to delete.

David

---

### Post by Gillingham on 2011-10-22
Peculiar irexec was the culprit.  I use it to provide commands from the remote control for my TV card to other programs.

Thank you for your help

David

---

