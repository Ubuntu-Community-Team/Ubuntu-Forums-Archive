---
title: "Can You please help noob with font size?"
date: 2006-02-02
forum: General Help
---

### Post by Aux on 2006-02-02
Hello! I've just installed Kubuntu 5.10. I want to make my fonts a bit larger like they are in Windows. How to do it? I have russian locale so every menu item is in russian. Maybe You can give application names like they are in main menu? Like Adept or KSystemLog? Thank You in adance!

---

### Post by glycoknob on 2006-02-02
There are several ways to do so.

In the Kubuntu Menu go to system settings, appeareance, fonts and adjust the size for all fonts. Don't know about the results. kcontrol is the way to go in terminal.

the second way is changing the resolution of your x-server. if you switch to 100dpi fonts will be in all applications bigger. You can change this to other resolutions besides 75 or 100dpi however its possible that you computer slows down a little bit due scaling.

edit /etc/kde3/kdm/kderc as super-user:

sudo kate /etc/kde3/kdm/kderc

and change the line:
ServerArgsLocal=-nolisten tcp 

to 
ServerArgsLocal=-nolisten tcp -dpi 100

and restart your x-server. Just tested this and fonts are in all applications bigger with no caveats in displaying or design.

good luck!

---

### Post by Aux on 2006-02-02
Thanks! Editing kderc really helped me!

---

