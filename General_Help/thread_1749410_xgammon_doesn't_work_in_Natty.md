---
title: "xgammon doesn't work in Natty"
date: 2011-05-04
forum: General Help
---

### Post by stevenleeconsulting on 2011-05-04
When executing xgammon: /usr/games/xgammon
 
The following error message occurs: 
 
couldn't load doubler dice font, using default, sorry
X Error of failed request: BadFont (invalid Font parameter)
Major opcode of failed request: 55 (X_CreateGC)
Resource id in failed request: 0x0
Serial number of failed request: 132
Current serial number in output stream: 134
 
Every other verion of Ubuntu runs xgammon properly except Natty, Ubuntu Release 11.04.
 
Any ideas or help would be appreciated.
 
Thanks,
Steven

---

### Post by sisco311 on 2011-05-04
Hi and welcome to the forums!

Hmmm... xgammon defaults to the helvetica font, which is not installed by default and fails to run with the default font.

It works for me with the *clean* font:
```
xgammon -doublerfont '-*-clean-*-*-*-*-*-*-*-*-*-*-*-*'
```

You can use the *xfontsel* utility to get the [XLFD]("http://en.wikipedia.org/wiki/X_logical_font_description") of the fonts known to your X server.

---

### Post by stevenleeconsulting on 2011-05-05
Thanks. That worked.

---

### Post by sisco311 on 2011-05-05
You're welcome!

BTW, I opened up a bug report here:[lpbug]778004[/lpbug]

---

### Post by yotam on 2011-12-26
Same experience for me. It was solved by installing [FONT="Courier New"]xfonts-75dpi[/FONT].

> **stevenleeconsulting said:**
> When executing xgammon: /usr/games/xgammon
 
The following error message occurs: 
 
couldn't load doubler dice font, using default, sorry
X Error of failed request: BadFont (invalid Font parameter)
Major opcode of failed request: 55 (X_CreateGC)
Resource id in failed request: 0x0
Serial number of failed request: 132
Current serial number in output stream: 134


---

### Post by stevenleeconsulting on 2011-12-26
Thanks for the updated information. I'll give it a try.

---

