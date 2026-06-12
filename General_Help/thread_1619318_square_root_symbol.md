---
title: "square root symbol"
date: 2010-11-11
forum: General Help
---

### Post by bzzzzz on 2010-11-11
I think this should be pretty easy, but I'm spending far too long hunting and can't seem to find the square root symbol using the altgr key.

I can find loads of useful things such as
¹²³³¾{½€½¾¡&#8539;¼¼&#8540;&#8541;&#8542;™±©
and even more that i'll never need, but can't find a square root

any help much appreciated.

---

### Post by houseworkshy on 2010-11-11
If you have open office you can insert it as a special character in writer.  That may be invalid as I don't know what application you want to use it in.

---

### Post by bzzzzz on 2010-11-11
That is useful and I will probably use that when writing documents.

However if I want to email somebody and include that symbol is it possible?

---

### Post by houseworkshy on 2010-11-11
It is.  If you search for "character map" in the help ( the ring symbol the top of the screen ) it explains it.  You can also copy and paste.  Open office formula is nice for playing with maths, also the default calculator has several modes.

Correction I've just noticed that you are on hardy, so for ring symbol read blue question mark.  Also top bar not top of screen.

---

### Post by bzzzzz on 2010-11-11
i'm actually on linux mint which is based on 10.04, just not updated my profile.

The character map thing does work, but it would be neat if I could do it at the press of a button.

Thanks for the help though.

---

### Post by houseworkshy on 2010-11-11
One can also asign key combinations but I'm not sure how in mint which is based on kde not gnome which is the one I use.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)  is handy.  Ive just tried a quick search for something similar which relates more to kde or mint but don't know where to look.  I did try mint once and remember that they'd packed the browser with links so maybe in there.  If unsucessful copy and paste from open office is nicer for emails anyway because the writing tool are better in a dedicated wp.  It is also worth looking at the helps in whatever email program you use.  Good hunting.

---

### Post by bzzzzz on 2010-11-11
You can get mint in kde and gnome.
The default is now gnome and has been for the last few editions.
Personally I've always been more comfortable with gnome.  

I'll continue hunting - but may use your work around when I really need it.

---

### Post by kyphi on 2010-11-11
Why not use Unicode?

Hold down Shift and Ctrl while typing u221a

The result = &#8730;

---

### Post by bzzzzz on 2010-11-12
Very nice that's what I'm after.  Why can't I program that to be one button.

For instance I don't think I'll ever need

& 

which is the symbol for alt gr shift k

&

It's identical to shift 7

---

### Post by mc4man on 2010-11-13
> program that to be one button.

Well if  the 'button' was a panel launcher  than it would be pretty simple to set up, though it does seem to be a bit of overkill to use just for a character, (unless you used it ALOT.

Edit: - forgot to mention what the launcher does (was very late
basically the command for launcher runs a small script  - uses xdotool to sim. key presses. Clicking  on launcher inserts &#8730; where ever the cursor is ( if in email, text file, here,  ect.

#!/bin/bash
xdotool keydown Ctrl+Shift
xdotool type u221a
xdotool keyup Ctrl+Shift

---

### Post by stinkeye on 2010-11-13
If you add the character pallet applet to the panel you can then edit it to add characters of your choice.
eg I added &#8730; to the section where ¹²³¼½¾ is shown.
You then just click on &#8730; in the panel and you can paste into whatever.

---

### Post by kyphi on 2010-11-13
This was one of those "intriguing" problems and after using "xev" to find the appropriate keycodes and using "xkeycaps" to remap the keyboard, I found a couple of much simpler solutions.  There is nothing wrong with re-setting the keys on your keyboard using the above-mentioned tools as long as you remember what has been done and know how to reverse it.
Keep in mind that when you do a fresh install all these configurations will be lost.

The following are less drastic:

1.  In OpenOffice, open Tools and then Autocorrect Options.  Place the "&" in the left field under Replace and the "&#8730;" in the right field under With and then click on New followed by OK.
The "&#8730;" I had cut after inserting it into a document using unicode u221a (with Ctrl+Shift).

To use in OOo, press on "&" and follow with Enter to get "&#8730;".

2.  In Thunderbird, use the "&" wherever you want a "&#8730;" and use Edit, Find and Replace and enter "&" in the Find Text and "&#8730;" in the Replace field.  Click on Replace All.

A caution to those reading this out of context - the OP wanted to use the "&" sign to get "&#8730;".

---

