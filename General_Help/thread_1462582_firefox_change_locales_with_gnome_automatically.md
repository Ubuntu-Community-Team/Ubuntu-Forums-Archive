---
title: "firefox change locales with gnome automatically"
date: 2010-04-25
forum: General Help
---

### Post by docjones2 on 2010-04-25
I have my 10.04 set up with english (us and gb) as well as spanish languages installed.

I have firefox 3.6.3 compiled and installed for a 64 bit system.  The firefox source code comes only with en-US locale, so I obtained en-GB.jar and es-ES.jar (as well as their manifests) from firefox.com and added them manually to my chrome directory.

This had worked in the past, when I'd logout and switch the gnome locale to es-ES firefox would come up in es-ES etc,  but for some reason firefox will only start up in en-US now.

How can I fix this to match the desired behaviour?

---

### Post by docjones2 on 2010-04-25
If I manually remove the en-US.jar and manifest, it will in fact use the other locales, so the locale files I have definitely work, it's just a matter of which locale firefox chooses at start time.

Does anyone know where/how firefox chooses the locale?  I have thunderbird installed as well, and it chooses the correct locale.

I'll continue my prodding, if I find a solution I'll let ya'll know

---

### Post by docjones2 on 2010-04-25
got it.

The configuration intl.locale.matchOS needs to be changed to true

do this by typing in the search bar "about:config"
then find "intl.locale.matchOS" and change the value to true

I don't know why it isn't true by default.... but who gives a damn, now its fixed!

---

