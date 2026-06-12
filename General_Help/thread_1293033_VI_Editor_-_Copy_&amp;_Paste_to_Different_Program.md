---
title: "VI Editor - Copy &amp; Paste to Different Program"
date: 2009-10-16
forum: General Help
---

### Post by johnterdi on 2009-10-16
I have 22 lines written in Vi. I'd like to know how I would be able to copy the lines and paste it over to a different program like open office writer. I tried 22yy but that only works if I want to paste it inside of Vi.

---

### Post by Giblet5 on 2009-10-16
Are you running in a terminal window, or the text console?

There is no cut/paste on the text console (no mouse either).

On a terminal window, select the text (left-click-and-hold at beginning, drag to end, release), right-click and select "Copy" from the menu...

If the text is too big for one screen, simply resize the window.

You can't spell "evil" without vi. Coincidence?

---

### Post by johnterdi on 2009-10-16
So Vi can't copy text over a page long? It can only copy what is displayed and not more than that? So to try and copy more, I would need to maximize the window and zoom out in hopes that all the text that needs to be copied is displayed in a single screen?

---

### Post by KlinerDraken on 2009-10-16
have you tried opening the file with nano or gedit?

---

### Post by kbielefe on 2009-10-16
You want to yank it into the + register (see :help registers for more info).

To yank 22 lines for pasting to other applications (note you type the double-quote):  "+22yy

Also works with marks.  On the first line, type:  ma
on the last line to copy, type:  "+y'a

Pasting from another application is "+p

Hope that helps.  I've been using vi for over 17 years and still learn something new quite often.

---

### Post by johnterdi on 2009-10-16
@KlinerDraken, thanks, but I'm looking for a way to copy the text directly inside Vi and making it possible to paste it into other apps.

kbielefe, that's exactly what I've been looking for. Thank you very much for the precise explanation. And thanks to all that responded!

It's time to hit the registers.


> **kbielefe said:**
> You want to yank it into the + register (see :help registers for more info).

To yank 22 lines for pasting to other applications (note you type the double-quote):  "+22yy

Also works with marks.  On the first line, type:  ma
on the last line to copy, type:  "+y'a

Pasting from another application is "+p

Hope that helps.  I've been using vi for over 17 years and still learn something new quite often.

---

