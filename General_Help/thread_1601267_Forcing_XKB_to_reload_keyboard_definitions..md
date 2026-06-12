---
title: "Forcing XKB to reload keyboard definitions."
date: 2010-10-20
forum: General Help
---

### Post by jwbrase on 2010-10-20
I've been working on writing up an XKB keymap for the Tai Viet script(Unicode block AA80 to AADF). I made several typos in defining the keyboard, resulting in mismatches of characters to keys. I have fixed these in the keyboard definition file in /usr/share/X11/xkb/symbols, but when I switch to the keyboard with setxkbmap, it keeps using my first, buggy layout. Apparently its caching a binary form of the keymap somewhere, and isn't rereading the keymap definition. Is there any way to force it to clear its cache or otherwise reread the definition from the edited file?

(I'm running Lucid upgraded from Jaunty, in case there are any differences in solutions for different versions).

---

