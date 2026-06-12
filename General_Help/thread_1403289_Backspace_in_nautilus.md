---
title: "Backspace in nautilus"
date: 2010-02-10
forum: General Help
---

### Post by colobix on 2010-02-10
Hey. in explorer you can use backspace as a shortcut key to go back the the under directory. How can I do that here in nautilus.

---

### Post by Satoru-san on 2010-02-10
Try System -> Pref -> Key Bindings.

---

### Post by colobix on 2010-02-10
> **Satoru-san said:**
> Try System -> Pref -> Key Bindings.

thanks but I tried but I can't find anything about nautilus or going back to last directory there.
ANy idea?

---

### Post by jken146 on 2010-02-10
Have a poke around in gconf-editor under apps->nautilus

---

### Post by colobix on 2010-02-10
> **jken146 said:**
> Have a poke around in gconf-editor under apps->nautilus
Who and what now?
SOrry I didn't understand that. and what is gconf-editor.
I don't wanna mess around and shït.

---

### Post by audiomick on 2010-02-10
> **colobix said:**
> Who and what now?
SOrry I didn't understand that. and what is gconf-editor.
I don't wanna mess around and shït.
It is an application for setting up the GUI.
If it is installed (don't know if it is there by default or not), you can start it in the terminal with
```
gconf-editor
```
but I just had a look and couldn't find anything that looked relevant.

---

### Post by jken146 on 2010-02-10
Press Alt+F2, type **gconf-editor** and press Enter. Look in apps-->nautilus in there for a setting that you think might do what you want.  That's where I think it would be, if there is a way to set a keybinding for 'back'.

BTW, did you try Alt+left_arrow? It works in Firefox.

---

### Post by audiomick on 2010-02-10
> **jken146 said:**
> Press Alt+F2, type **gconf-editor** and press Enter. Look in apps-->nautilus in there for a setting that you think might do what you want.  That's where I think it would be, if there is a way to set a keybinding for 'back'.

BTW, did you try [COLOR=Red]Alt+left_arrow[/COLOR]? It works in Firefox.
works for me.

---

### Post by colobix on 2010-02-10
I didn't understand the editor, atleast couldnt find anything there but Alt+left works. THanks.

Ok so now, how do I change Alt+left to backspace? Since that's what I am used to. I couldn't find it under the keybinder thing.

---

### Post by mechro on 2010-02-10
Go to **System > Preferences > Appearance: Interface**. Check the box marked **Editable menu shortcut keys**.

Open Nautilus... browse to any folder so that your **back button** is activated... in the **Go** menu, hover your mouse over the **Back** item so that it is highlighted... press Backspace... Voila!

---

