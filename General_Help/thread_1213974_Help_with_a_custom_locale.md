---
title: "Help with a custom locale"
date: 2009-07-15
forum: General Help
---

### Post by _Q_ on 2009-07-15
Is there a locale rules expert here? :)

I would like to make a custom locale out of the current one..
I cloned my current locale (from /usr/share/i18n/locales) and tried to twigle with the rules... (without any success)
The idea is to change the sorting order of characters, so that chars "[" and "]" are before numbers and letters.
(so that means I'm editing the LC_COLLATE section)

Locale is using iso14651_t1 as a template...
(copy "iso14651_t1")

ASCII == UTF
[ == U005B
] == U005D

If this is out of the scope of the forum, please suggest where to ask :)

---

