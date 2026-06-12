---
title: "mrxvt + midnight commander and ncmpc"
date: 2006-04-13
forum: General Help
---

### Post by 3david on 2006-04-13
Hi,

i've just installed mrxvt, i've been playing with it's config, and it's really great,
like gnome-terminal but a lot faster,

i've been having two problems with it though:
1. when i run mc or ncmpc (music player daemon ncurses ui) i get squares instead of the bars (i actually get two squares per one bar).
2. i can't type in hebrew, if i try to type i get wierd two wierd characters for every hebrew char i type (hebrew typing works on all gtk apps, so the hebkeyboard is set correctly)

I tried running mrxvt with: "LC_CTYPE=he_IL mrxvt", but then when i type hebrew it just ignores the keys, nothing happens.

the font i'm using for it is "Bitstream Vera Sans Mono" and i've attached my Xdefaults file to this message.

Any ideas?

**Update:** i've installed the "language-pack-he" package, and now i have the "he_IL.utf8" locale, i tried using it, but i get the same problem as with en_US.utf8 (i type a hebrew char and i get two chars, so typing 3 or 4 chars gives me something like this:   ×¢×&#8216;×¨×&#8482;)

---

