---
title: "Dell computer keyboard problem"
date: 2009-09-16
forum: General Help
---

### Post by lanzcc on 2009-09-16
Hello

No matter how many manual pages I read, or how many searches I do, I cannot seem to get a complete answer to my problem. Every partial answer leads to some dead end or other. Pardon me I have no apostrophe.

My Dell Inspiron 1520 keyboard doesnt work with any of the provided keymaps.

I cant get authorization to save a new xmodmap that has my own needs entered.

Can anyone tell me how to permanently change the keyboard mapping? Usually in the ones that come close - like xmodmap.uk or xmodmap.us_intl there are half a dozen keys that are incorrectly mapped. Unfortunately, ONE of them makes C programming possible, and the OTHER makes Ubuntu command-line use possible

I have read every document I can find. I&#472;e searched with every keyword I could think of. Oh there you see : I&#472;e comes out pretty weird

I would be satisfied if I could even enable the down key from .uk, because its only problems are the end key which i can live without and the double-quote and @ which are reversed, and I can live with that, too, but jezz, you NEED that down key sometimes.

HELP HELP PLEASE OH GOD HELP

Lanzcc
[EMAIL="lanzcc@potsdam.edu"]lanzcc@potsdam.edu[/EMAIL]

---

### Post by P4man on 2009-09-17
Thats annoying indeed.
Anyway, i assume you tried changing those keys with xmodmap? If you want those changes to be applied on boot, put them in:
~/.Xmodmap

---

