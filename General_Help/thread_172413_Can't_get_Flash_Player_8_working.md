---
title: "Can't get Flash Player 8 working"
date: 2006-05-08
forum: General Help
---

### Post by Dr. Feelgood on 2006-05-08
I used to be able to watch all kinds of flash videos without a problem but now all of a sudden I get a black screen that says download Flash Player 8.  I do exactly as it says and I have the two correct files in the pluigins directory (so and xpt or something like that) but still nothing.  What the hell is going on?

---

### Post by adrenaline on 2006-05-08
Interesting.  I entered this:

```
sudo apt-get install flashplugin-nonfree
  sudo update-flashplugin
```

then moved the 2 files and worked for me earlier today.

EDIT:  Nevermind, must be flash 7.  Flash 8 videos don't work.

---

### Post by jazzmuzik on 2006-05-08
Version 8?

You can type 'about:plugins' (damn smileys; that supposed to be about : plugins without any spaces) into Firefox and it'll show all your installed plugins. If you don't see Flash then FF isn't finding it.

Exactly what directory are you installing the plugins into?

---

### Post by DoktorSeven on 2006-05-08
Unless things have changed very recently, there's no Flash Player version 8 for Linux; from what I understand, they're waiting until 9 is released to do another Linux version.

This means that all Flash videos that require version 8 won't work until the Linux upgrade comes around.  In the meantime, I use Firefox (Windows version) + Flash 8 under Wine which seems to work well enough.

---

### Post by Dr. Feelgood on 2006-05-08
[QUOTE=DoktorSeven]Unless things have changed very recently, there's no Flash Player version 8 for Linux; from what I understand, they're waiting until 9 is released to do another Linux version.

This means that all Flash videos that require version 8 won't work until the Linux upgrade comes around.  In the meantime, I use Firefox (Windows version) + Flash 8 under Wine which seems to work well enough.[/QUOTE]


Shit....well I guess there's my answer.  Damn.

---

### Post by KingArthur10 on 2006-05-28
Don't dispair!  If you install wine, then install both firefox for windows and the macromedia flash for Windows.  Now you can watch flash 8 files in linux :-)

---

