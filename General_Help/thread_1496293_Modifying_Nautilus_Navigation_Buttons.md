---
title: "Modifying Nautilus Navigation Buttons"
date: 2010-05-29
forum: General Help
---

### Post by iNsOmNiOuS on 2010-05-29
Hi,

Does anyone know how to modify the Nautilus Navigation buttons :

[IMG]http://www.freeimagehosting.net/uploads/02f8353651.png[/IMG]

Is it related to the theme ? If so how can I modify them. Thanks :D

---

### Post by UberStudent on 2010-05-29
What is it you're wanting to do? Remove some buttons? 

You can't do that with a dialog, as with, say, Firefox. You have to modify nautilus code in several places.

If that, perhaps Nautilus Elementary's [http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html](http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html)  mods will suit your needs.

Mere appearance of the buttons is controlled by the theme, and you can additionally theme the nautilus places menu.

Please be more specific.


----------------

---

### Post by iNsOmNiOuS on 2010-05-29
Sorry i wasn't specific enough. I want to change the buttons (Use a custom image for the back / forwards button)

---

### Post by UberStudent on 2010-05-29
System installed icon themes are at /usr/share/icons and locally installed ones are in a corresponding hidden folder in your home directory. You'll have to look for the specific  icons and replace them with same-sized ones. Sometimes icon themes inherit icons from other locations, though. To find all of them open the index.theme file of the icon theme in a text editor and have a look.

---

### Post by thongstele on 2010-11-21
How can I move navigation buttons near together, like in Finder of Mac OS. (sorry for this question, because i know that everyone don't love Mac.) Thx in advance.

---

