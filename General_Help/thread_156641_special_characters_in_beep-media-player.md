---
title: "special characters in beep-media-player"
date: 2006-04-07
forum: General Help
---

### Post by dee.dw on 2006-04-07
Hello,

I'm using the standard version of bmp from Ubuntu servers. But how can get this player to show special chars such as German ä=ae, ö=oe, ü=ue or skandinavian letters correct? I only get an question mark at this position...

This happens with MP3s with the remark "invalid utf8-encoding" but also (and that's the annoying thing) with radio streams.

I couldn't find the solution in the forum, maybe nobody has this problem but me ???

Greetings, Dee

---

### Post by dee.dw on 2006-04-07
Ah, finally I found the FAQ of BMP and partly the solution: [Link](http://bmp.beep-media-player.org/index.php/FAQ#Why_do_I_have_.22.3F.3F.3F_.28Invalid_UTF-8.29.22_in_the_playlist.3F).

German special chars are no problem now because I use [encodings](http://www.openi18n.org/subgroups/sa/locnameguide/final/CodesetAliasTable.html) ISO-8559-1 und ISO-8559-15. But did anyone know the settings for scandinavian or eastern europe chars?

Greetings, Dee

---

### Post by adamkane on 2006-04-07
Ubuntu uses UTF-8. BMP still uses ISO-8859-X.

Soon all media players/managers including BMP will be able to read both UTF-8 and ISO-8859-X, and soon all media players/managers will write ID3 tags and filenames in UTF-8 by default.

We are in a transition period from ISO-8859-X to UTF-8. The standard is UTF-8, so be prepared for what's coming.

---

### Post by dee.dw on 2006-04-08
Eh, yes... does that help with my problem now?

Greetings, Dee

---

### Post by Versusnja on 2007-10-12
Hi!
Your link worked like a charm. All my CP1251 files are displayed correctly (converted on the fly to UTF-8).

(BMP is a great peace of software I must say.)

---

