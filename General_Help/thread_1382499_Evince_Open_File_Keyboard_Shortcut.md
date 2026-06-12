---
title: "Evince Open File Keyboard Shortcut"
date: 2010-01-16
forum: General Help
---

### Post by eabod on 2010-01-16
For some reason, Evince has the open file keyboard shortcut set to "A", which means that if I'm searching for text in a pdf and I type the "a" key, the "Open Document" dialog box is called. How can I fix this?

Thanks.

---

### Post by n0dix on 2010-01-16
what is the version of Evince? You tried reinstall the program?

---

### Post by eabod on 2010-01-16
> **n0dix said:**
> what is the version of Evince? 
"Document Viewer 2.28.1"
> **n0dix said:**
> You tried reinstall the program?
Yes, and the problem persisted.

---

### Post by cben on 2010-02-17
It seems that you have Gnome Editable Shortcuts feature turned on and accidentally changed the shortcut for File&#8594;Open.  The feature means that while you have a menu open, pressing any keyboard key sets it as the shortcut for the currently selected action (Backspace removes a shortcut).  

**To fix it:** just open the File menu and while the mouse is over the Open action, press Ctrl+O.  This should restore the standard shortcut.

You can also remove [FONT="Courier New"]~/.gnome2/accels/evince[/FONT] to restore all Evince shortcuts to defaults (that directory stores one text file for each application whose shortcuts you've edited).

This feature very powerful if you like adding/customizing shortcuts, but sometimes happens accidentally.  Your case is particularly common: you probably pressed "Alt+F, A" trying to activate File&#8594;Save As - but evince doesn't have such a menu item (File&#8594;Save does it), so instead the "A" changed the shortcut for File&#8594;Open!  You can disable this feature entirely in *System&#8594;Preferences&#8594;Appearance dialog &#8594; Interface* tab &#8594; *Editable menu shortcut keys* checkbox.

---

### Post by cben on 2010-02-17
> **cben said:**
> 
You can also remove [FONT="Courier New"]~/.gnome2/accels/evince[/FONT] to restore all Evince shortcuts to defaults (that directory stores one text file for each application whose shortcuts you've edited).


Correction: this one doesn't work.  I have it on my system but changing evince shortcuts isn't reflected in the file, and removing it didn't reset the shortcuts.  I was unable to discover where it's stored.

Anyway, pressing Ctrl+O over the menu item short restore it.

---

### Post by mdwy62 on 2010-05-10
Had exactly the same problem. Thanks for the fix. I reset File>Open menu item and disabled editable shortcut keys and can again search for words in a document with an "a" in them.

---

