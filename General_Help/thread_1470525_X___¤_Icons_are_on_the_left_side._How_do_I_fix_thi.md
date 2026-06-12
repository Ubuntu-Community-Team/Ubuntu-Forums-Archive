---
title: "X _ ¤ Icons are on the left side. How do I fix this thing?"
date: 2010-05-02
forum: General Help
---

### Post by kokkus on 2010-05-02
Is there any possible way to fix this problem?
It's very frustrating.
And I honestly think this is one of the dumbest changes ubuntu have ever done.

---

### Post by WorMzy on 2010-05-02
See solution #2 in this thread: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by kokkus on 2010-05-02
Thanks but I couldn't find that option in the menu.
Can I fix this from the terminal?

---

### Post by arsenic23 on 2010-05-02
There is a way to change it using only the terminal... I don't remember where I saw that.  But you can also change it using gconf-editor.

It's the value under Apps > Meticity > general > button layout

Change the string there to put your buttons wherever you might like.

---

### Post by WorMzy on 2010-05-02
You couldn't find Appearance under System -> Preferences? Try pressing Alt+F2 anf running 'gnome-appearance-properties %F' (no quotes).

Another fix is to use gconf-editor (press Alt+F2 and run 'gconf-editor'), in gconf-editor browse to apps/metacity/general, and change the key "button_layout" to ':minimize,maximize,close'.

---

### Post by Jeff Anthony on 2010-05-02
Google search may have been quicker but have you tried 

```
gconf-editor
```
apps > metacity > general > button_layout (double-click)
Value = ```
menu:maximize,minimize,close
```
OK button

---

### Post by akand074 on 2010-05-02
```
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```

---

### Post by kokkus on 2010-05-02
> **Jeff Anthony said:**
> Google search may have been quicker but have you tried 

```
gconf-editor
```
apps > metacity > general > button_layout (double-click)
Value = ```
menu:maximize,minimize,close
```
OK button

That helped but the icons are still on the wrong side.

And yes I can find the theme settings and stuff but that didn't change it back to right side. It just changed the window border theme.

---

### Post by akand074 on 2010-05-03
Have you tried my suggestion?

---

### Post by kokkus on 2010-05-03
> **akand074 said:**
> Have you tried my suggestion?
That does the same thing as what Jeff told me but yes.
Now I have Minimize, Maximize, Close but on the wrong side.
That could work for me if I only had Ubuntu but I am dual booting with win7 ,so it will still confuse my brain.

EDIT: Oh I figured it out. IT works now.
Thanks alot akand074 and you all.

The solution is basicly
gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

---

### Post by akand074 on 2010-05-03
What side are you trying to get it on? The command I gave you should bring it to the right side.

---

