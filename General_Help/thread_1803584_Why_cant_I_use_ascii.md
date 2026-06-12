---
title: "Why cant I use ascii?"
date: 2011-07-13
forum: General Help
---

### Post by Primitive Artifice on 2011-07-13
This my first time using a non-windows os. I have always been interested in using a linux based system so at my last reformat I decided to install ubuntu. Ive run into a few problems but one of the more inconvenient is my inability to use ascii (alt+83 for instance). Im missing a few keys on my keyboard (s and apostrophe) so using ascii was the simplest way to compensate for that. Unfortunately it doesnt seem to work anymore.

Is there anyway to get ascii to work on my computer again or is there a reasonable alternative (trying to avoid onscreen keyboards if possible).

---

### Post by grahammechanical on 2011-07-13
Have you tried going to System Settings>Keyboard>Layouts and choosing another keyboard or other layouts. They can be selected by language or by country. There may be a layout variation that gives you the keys you want.

Regards.

---

### Post by haqking on 2011-07-13
take a look at compose key.

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by WorMzy on 2011-07-13
Also, enter unicode characters with Ctrl+Shift+u, followed by the number.

e.g.

Ctrl+Shift+u, 165 = &#357;
Ctrl+Shift+u, 2103 = &#8451;

---

### Post by jwbrase on 2011-07-13
> **Primitive Artifice said:**
> This my first time using a non-windows os. I have always been interested in using a linux based system so at my last reformat I decided to install ubuntu. Ive run into a few problems but one of the more inconvenient is my inability to use ascii (alt+83 for instance). Im missing a few keys on my keyboard (s and apostrophe) so using ascii was the simplest way to compensate for that. Unfortunately it doesnt seem to work anymore.

The alt+[number] method of typing characters isn't called "ASCII" (it's called "alt-codes"), and it's a Windows only feature. On Linux, GTK+ programs (most of what you'll be using probably, if you're using standard Ubuntu with the GNOME interface) allow you to use the ctrl-shift-u method described by WorMzy.

Note, however, that the number has to be input in hexidecimal, e.g ctrl-shift-u-e4 rather than alt-0228, and that it uses Unicode instead of Windows-1252, so that the characters that you get with Alt-0128 through Alt-0159 on Windows require entirely different numbers (not just converted to hexidecimal). The Wikipedia article on [Windows-1252]("http://en.wikipedia.org/wiki/Windows-1252") has a table that gives the Unicode values for Windows-1252 codepoints. 

(Also remember that Alt-0[number] and Alt-[number] will give you potentially different results on Windows. Alt-0[number] gives you the corresponding Win-1252 character, Alt-[number] gives you a character from a DOS codepage).

---

### Post by haqking on 2011-07-13
[http://alt-codes.org/linux/](http://alt-codes.org/linux/)

---

### Post by Primitive Artifice on 2011-07-13
Ah, thank you very much for the help guys. I apologize for incorrectly referring to it as ascii, I'm a bit behind on computers so terminology and the like are a bit beyond me at the moment.

It seems unicode is my best bet and I've already started using it to compensate for my missing keys. Thank you again for all your help.

---

### Post by The Cog on 2011-07-13
If you're stuck finding a character/code, look at the application **Accessories / Character Map**. It's got vast numbers of characters, and gives you the unicode values for them.

---

