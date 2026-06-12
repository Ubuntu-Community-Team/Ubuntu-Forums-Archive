---
title: "Register Iron as a program?"
date: 2010-07-21
forum: General Help
---

### Post by turgidtoupee on 2010-07-21
Sorry for the ambiguous title, but it's kind of hard to describe in a few words.

My question is how to make srware iron behave in such a way as if I had installed a .deb file of it. Like, appear in all the menus, appear in the deskbar, etc. There's got to be a way, I just don't know what it is.

I tried searching, but it came up with nothing as I didn't know what to search for.

---

### Post by endotherm on 2010-07-21
um, how are you installing this program?

keep in mind, it is up to the developer and packager as to whether an app creates desktop/applications menu entries by default. a .deb may create them or not, depending on how the install routine is coded.

so, am i completely missing your question?

---

### Post by turgidtoupee on 2010-07-21
> **endotherm said:**
> um, how are you installing this program?

keep in mind, it is up to the developer and packager as to whether an app creates desktop/applications menu entries by default. a .deb may create them or not, depending on how the install routine is coded.

so, am i completely missing your question?

It's just an executable in a folder with all its files. 

This functionality would be useful to me as I'd like to do the same with dwarf fortress and minecraft.

I can add them to the menus manually but I'd quite like to add them to the deskbar too since I use that as my primary application launcher.

---

### Post by Vaphell on 2010-07-21
you can add stuff to system menu by rightclicking and modifying it

also i think that apps register themselves with .desktop files, goto /usr/share/applications and look at some examples (there are plenty of them)

---

### Post by turgidtoupee on 2010-07-21
> **Vaphell said:**
> you can add stuff to system menu by rightclicking and modifying it

also i think that apps register themselves with .desktop files, goto /usr/share/applications and look at some examples (there are plenty of them)

I've created one for iron in there, but it still doesn't appear. Do I have to restart, or do anything else?

EDIT: Never mind, it was just me doing it wrong. Should have just created one from scratch and copied most of it over. It now appears in menus but won't start in the deskbar, or with alt-F2.

FURTHER EDIT: With some sniffing around, I created a link in /usr/bin. Now works excellently.

---

### Post by endotherm on 2010-07-23
Have [fun]("http://df.magmawiki.com/index.php/DF2010:Losing") with the dwarfiness

---

