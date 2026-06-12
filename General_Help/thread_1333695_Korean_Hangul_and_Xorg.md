---
title: "Korean Hangul and Xorg"
date: 2009-11-21
forum: General Help
---

### Post by Gwasanaethau on 2009-11-21
&#50504;&#45397;&#54616;&#49464;&#50836; (Hi all)!

Here's an interesting one for you: I am learning Korean and like to write Hangul using the computer. I had a keymap set up and everything, and it worked for a while. However, I've noticed that the latest version of Ubuntu (and Arch, which I use) seems to separate the character blocks (Jamo). An example of this was in my signature: &#4363;&#4449;&#4523;&#4363;&#4449;&#4364;&#4462;&#4361;&#4454;&#4363;&#4461; (it should look like: &#50504;&#50500;&#51452;&#49464;&#50836;)!

For those of you who don't know, Hangul can be written using a computer in two ways: by using syllable blocks (like I did above &#8211; unicode code points U+AC00-U+D7A3 &#8211; Yes, that's over 11,000 different symbols!), or by using Hangul's 'complex script' feature.

Using the complex script feature, there is only a requirement to learn the 20 unique symbols (letters) and place them in the right order. The software will then combine them into blocks just like that above. This is much easier than using the syllable blocks because it can be done with a standard UK keyboard. ;)

However, an upgrade from Hardy to Karmic seems to have broken this feature. I originally thought it might have been caused by going from GNOME 2.26 to 2.28, but LXDE on Arch does the same. Could it be a problem with the new release of X.org?

Sorry for the long post. Any thoughts, ideas or questions are welcome!

---

### Post by Gwasanaethau on 2009-11-24
For anybody who was wondering, I've solved this to a certain extent. I didn't realise you could use SCIM in combination with XIM (I use XIM for writing in Cyrillic, and for using Greek letters in equations). It's nowhere near as slick as the XIM setup I had, but at least it works. It still uses the huge U+AC00-U+D7A3 block though, so I guess I didn't really solve the underlying problem).

---

