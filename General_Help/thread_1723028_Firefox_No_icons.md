---
title: "Firefox No icons"
date: 2011-04-06
forum: General Help
---

### Post by sandyd on 2011-04-06
Im currently missing all the icons in the firefox download window. Ive made it appear once before, so I know its possible. But since then, ive reinstalled.

Any ideas?

---

### Post by WorMzy on 2011-04-06
Check the gconf entry "/desktop/gnome/interface/menus_have_icons". Make sure it's enabled, then restart firefox.

I *think* this will fix it.

---

### Post by sandyd on 2011-04-09
> **WorMzy said:**
> Check the gconf entry "/desktop/gnome/interface/menus_have_icons". Make sure it's enabled, then restart firefox.

I *think* this will fix it.

Nope. doesnt work.
i might mention that im using KDE

---

### Post by WorMzy on 2011-04-09
Might want to use the kubuntu title prefix next time then. ;)

Although I tested it myself, and it didn't work here either. I also can't find anything in about:config that looks like it could toggle icons in the download manager. Maybe you installed an extension last time?

---

### Post by lidex on 2011-04-10
Does kubuntu use Ubuntu Firefox Modifications - you could try removing that. Or localstore.rdf from your profile folder with firefox closed. Have you tried a new profile?

---

### Post by sandyd on 2011-04-10
> **lidex said:**
> Does kubuntu use Ubuntu Firefox Modifications - you could try removing that. Or localstore.rdf from your profile folder with firefox closed. Have you tried a new profile?
yup. 
Ive removed the firefox modifications already, and its a new firefox profile

---

