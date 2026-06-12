---
title: "SCIM went crazy when moving to 9.10"
date: 2009-12-26
forum: General Help
---

### Post by desperateone on 2009-12-26
So I'm considering using IBus, seeing as it's the *de facto* standard now. Two questions;
1) I played around with IBus, but I can't get it to work. Are there any setup tutorials? (for Japanese)
2) Is it safe to remove all the scim-* packages now?

---

### Post by desperateone on 2009-12-26
Bump!

---

### Post by Irihapeti on 2009-12-26
Scim still works on 9.10 - I've got it installed and it behaves fine. Did you upgrade from 9.04 or do a fresh install? That might make a difference.

If you want to use iBus, you can remove the Scim packages. You can also leave Scim installed and switch between the two if you wish. (Only one can be active at a time, of course.)

To set up iBus for Japanese, you need to install:

ibus
ibus-anthy
ibus-gtk
anthy
ibus-qt4 (if you use qt applications)

You select iBus as your input method by going to System -> Administration -> Language Support and choosing "ibus" in the "Keyboard Input Method System" box.

To set up iBus itself, go to System -> Preferences -> IBus Preferences. Click on the Input Method tab and then the "Select an Input Method" box. Scroll down to Japanese and then select Anthy with the gold crown logo. (see first screenshot) Remember to click on "add" so that it gets added to the list of methods in the main "input method" box. (Second screenshot)

Now log out and in again (or reboot if you prefer) and iBus should be working. Open a document and press ctrl-space and you should get a panel in the lower right-hand side of the screen, rather like the Scim one.

If you need any further help, or you'd like to know how to get Scim working as well, please ask.

---

