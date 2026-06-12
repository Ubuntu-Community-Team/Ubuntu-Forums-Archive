---
title: "Weird problem with Emacs23"
date: 2009-11-23
forum: General Help
---

### Post by FLMKane on 2009-11-23
Before I start I am a heavy user of emacs. I would not appreciate anyone telling me to switch to vi(or anything else).


I tried to install emacs23 on 9.10, using the Ubuntu software centre. It worked but when I started emacs, it looked really wierd. The font size was MASSIVE. I mean it looked like this:

[http://i197.photobucket.com/albums/aa139/FLMKane/Screenshot.png?t=1258994825](http://i197.photobucket.com/albums/aa139/FLMKane/Screenshot.png?t=1258994825)

I cant work with that. I tried compiling from source, but there was no difference. So I've gone back to emacs22, but I would really, really like to use emacs23 again. I'll be honest with you, I really like the new pretty fonts in emacs 23, they make me squint a lot less.

So whats the fix?

---

### Post by Giblet5 on 2009-11-23
That's not emacs. The emacs editor is a text-based editor. That's x11emacs, so set a smaller font for x11emacs.

Or, open a terminal window and run emacs from there like the developers intended. ;)

---

### Post by FLMKane on 2009-11-23
> **Giblet5 said:**
> That's not emacs. The emacs editor is a text-based editor. That's x11emacs, so set a smaller font for x11emacs.

Or, open a terminal window and run emacs from there like the developers intended. ;)

I cant tell whether this is a joke or not. I've used emacs from the terminal but... how do you set a smaller font? I mean I did go to the menu and do it but it didn't work.

---

### Post by lykwydchykyn on 2009-11-23
Can you post your ~/.emacs file?

---

### Post by FLMKane on 2009-11-23
Um I fixed. I just set the default font really low(1). Thank you.

---

