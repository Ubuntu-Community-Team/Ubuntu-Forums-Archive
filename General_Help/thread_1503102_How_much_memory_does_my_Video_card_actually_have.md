---
title: "How much memory does my Video card actually have??"
date: 2010-06-06
forum: General Help
---

### Post by samstreet101 on 2010-06-06
My problem/concern is this: I have an ATI Radeon HD 3870 with 512MB GDDR or so I thought. See when I check the detailed specs in either the hardware information tool or by using $ lspci or $lspci -v they both give me a breakdown of my video card and say that i have 256MB of 'prefetchable' memory. Now it may be that the term prefetchable is throwing me off but could anyone enlighten me as to why this should be? Wierdly when I check my video card out in my windows partition it identifies that it has 512MB...

Any thoughts?

---

### Post by warfacegod on 2010-06-06
At a guess, I'd say your card has 256 MB RAM on it and is "borrowing" another 256 MB from your system RAM. ATi was fond of this sort of thing, a few years ago. It made it so that they could advertise their cards as better than they really were. From what I understand, the practice is still used but now they're showing the real amount of RAM the card has is "optionally" increasable from your system RAM. I believe nVidia did and has been doing the same thing to a lesser scale.

---

### Post by warfacegod on 2010-06-06
F.Y.I. Using a computer while taking a bath is, generally speaking, never a good idea.:biggrin:

---

### Post by sdennie on 2010-06-06
The above explanation sounds right.  To me, "prefectable" is a polite way of saying, "We are using system RAM but can try to prefetch it to L2/L3 so you don't notice the performance hit".

---

### Post by Leppie on 2010-06-06
from what i've understood of prefetchable memory is, that this is the part of the memory that uses caching.
in this case it could coincide with what was stated before, as system ram assigned as video ram would not be cached by the video card.

you can easily check this, by comparing the amount of ram installed in your machine with the amount of ram the system indicates. if 256mb are borrowed for video, you will have 256mb less ram.

---

### Post by samstreet101 on 2010-06-06
Thanks for the replies guys, so basically in a nutshell...i've been had! or at least, sort of been had. Actually this would explain why the nVidia card in the PC i use at work (running windows 7) says it has 3GB of ram!

---

### Post by sdennie on 2010-06-06
> **samstreet101 said:**
> Thanks for the replies guys, so basically in a nutshell...i've been had! or at least, sort of been had. Actually this would explain why the nVidia card in the PC i use at work (running windows 7) says it has 3GB of ram!

I wouldn't go so far as to say you've been had.  Unless you bought the card specifically for doing video RAM intensive things, whatever numbers it's reporting are probably fine.

---

