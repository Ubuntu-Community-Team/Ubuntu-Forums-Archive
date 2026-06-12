---
title: "Esperanto input problems"
date: 2011-11-17
forum: General Help
---

### Post by DarkerStar on 2011-11-17
Recently - following an upgrade to 11.10 - my Esperanto input method has stopped working properly. (Actually, the whole input system is behaving weirdly.*)

Normally to get accented characters in the x-system, you type the base character, then x. So, to get "&#349;", I type "sx". If I type any other character after the base character, I get the two characters. So, if I type "st", I get "st". So, if I type:
```
"Mi sercxas respondon."
```
I (used to) get:
```
"Mi ser&#265;as respondon."
```
What I get now is:
```
"Mi esra&#265; srepsondon."
```

It looks like if I type anything before the character is "locked in", the character I typed *after* comes out before the generated character. So if I type "s", it's in limbo until I either hit enter or "x" twice (to get "sx"). If I type anything else, that comes first, then the "s". So "Mi ser" becomes "Mi s<waiting for x>e<outputs e, then s>r" and I get "Mi esr", like you see above.

Was the input method system changed in the last version or so of Ubuntu? Because this used to work in all versions from 7.04.

(* When I say the input system is behaving weirdly, for example: CTRL+SPACE activates the input system... which is Esperanto by default. If I want to change to another input system - Anthy, for example - I try to click on the "e&#293;o-cx" logo in the floating box, get a list of installed input methods, click on Anthy, and nothing happens. If I actually want to change to Anthy, I first have to click the input method icon in the system tray, select Anthy there (nothing happens), **then** click on the "e&#293;o-cx" logo in the floating box and select Anthy, and it will *sometimes* switch to Anthy.)

---

