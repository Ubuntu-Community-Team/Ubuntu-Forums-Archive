---
title: "Firefox + Plugins + Ctrl Key Shortcuts"
date: 2010-09-12
forum: General Help
---

### Post by veaudaux on 2010-09-12
For whatever reason, embedded media in Firefox doesn't "see" keyboard shortcuts utilizing the Ctrl key.

I can reproduce this behavior consistently. For instance, copying and pasting via keyboard shortcuts (Ctrl + C, Ctrl + V) doesn't work in the java version of LogMeIn. Also, any Adobe Flash game that utilizes Ctrl key shortcuts fails to respond to the keypresses.

Of note, Ctrl by itself works as expected.

Is there anything I can do to remedy this?

---

### Post by jonathanbrickman0000 on 2011-07-19
Not a remedy, but a good workaround.  If you hold down Alt and press 0-2-2 on your numeric keypad, you send Ctrl-V; if you use 0-1-9, that's Ctrl-S.  These are the old ASCII control code equivalents.  If 0-2-2 and 0-1-9 don't work for you, try adding one more zero, i.e., 0-0-2-2 and 0-0-1-9; in some non-U.S. keyboard situations this may well be necessary.

---

### Post by mikejonesey on 2011-07-19
it is standard behaviour of flash/activx components to steal the keys... all you can do about it is install a firefox addon called noscripts...

---

### Post by Trolen on 2011-07-19
And where can we find this add-on ?

I can't find it.

---

### Post by lovinglinux on 2011-07-19
> **Trolen said:**
> And where can we find this add-on ?

I can't find it.

Type *about:addons* in the address bar or click *Tools >>> Add-ons* in Firefox menu or hit *CTRL+SHIFT+A*, then type the name of the add-on in the search.

---

