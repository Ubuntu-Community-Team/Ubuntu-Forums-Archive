---
title: "Problem with quotes, deadkeys (choosing keyboard layout does&#324;t help)"
date: 2009-12-05
forum: General Help
---

### Post by Wotr on 2009-12-05
Hello all,

Anyone who has ever used an international keyboard layout must have noticed the ¨dead key¨ behaviour, where characters like quotes, double-quotes, tildes etc. wouldnt be typed when you press the key. Instead, it would try to add the quote as an accent to the letter-key you would type after it (like á). If you want a quote, press the quote-key twice.

I find this behaviour unbelievably annoying, so normally I would go to System --> preferences --> keyboard and choose keyboard layout ¨USA¨. That would fix it.

But not anymore.... no matter what keyboard layout I choose, the strange quote behaviour persists.

What makes this extra annoying is that the quotes produced after pressing it twice are not the ¨normal¨ quotes (like ASCII 34), but some unicode character that shell scripts and the terminal don´t understand.

Can anybody help me out?

Greets,

Wouter

---

### Post by Wotr on 2009-12-19
Still having this problem... 2 more things that seem strange:

1. The problem comes and goes. It was gone for a while but now it&#347; back again :|
2. It seems that the chosen keyboard layout in gnome-keyboard-properties is ignored completely. For example: if I choose a UK layout (which would have a double-quote over the 2) it still prints a @ when I press shift-2.

Am I really the only one with this problem? It is unbelievably annoying.

---

### Post by koolair on 2010-01-04
Yes, Im having this problem too...as you can see, no apostraphe mark after the I.

I cant use the quotation mark either.  Tilde doesnt work.  the (at) symbol which should be shift-2 is the quotation mark.  Question mark is shift-6.  This is really annoying!  Hope someone can help!!!

Joe

---

### Post by Wotr on 2010-02-07
Finally... a solution.

My first mistake is choosing the "us_intl" layout during installation. This is one of the layouts that uses "dead keys". It seems that, once you've chosen it, you're stuck with it forever. You can try to remove it using gnome-keyboard-properties, but it'll just come back.

Now, you can add another layout, but as I mentioned before, the system will just refuse to use it.... until I discovered that under "Layout options" you can choose "key(s) to change layout". I set that to "both alt keys together" (both for "us" and "us_intl", and sure enough, pressing alt-alt will change the keyboard lay-out!

It still changes back to us_intl from time to time, but pressing alt-alt changes it back instantly.

Hope this helps anyone.

---

### Post by Lady_Talia on 2010-02-26
THANK YOU!!!!!!

This had me so frustrated, I almost installed Windows again, just so I could use quotation marks properly. I would never have thought to check the layout of the keyboard because I did the keyboard test thing when installing and assumed that it would test for any discrepancies like that. Again thank you!

---

