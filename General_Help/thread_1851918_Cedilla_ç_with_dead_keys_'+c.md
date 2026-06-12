---
title: "Cedilla ç with dead keys '+c"
date: 2011-09-29
forum: General Help
---

### Post by aylons on 2011-09-29
This is an old problem for Brazilians using Ubuntu: the USA International Keyboard spans a "&#263;" if you try '+c.

This may seen logical for US users, but Brazilian users are very used to type "ç" with '+c. Combinations like Alt+C, AltGR+C gives a terrible user experience - typing two keys simultaneously is better left for shortcuts or seldom-typed symbols, not for a diacritic that happens in almost every sentence.

For years I have been using well-known, hacks for this, mostly editing /usr/lib/gtk-2.0/2.10.0/gtk.immodules as described in [http://wiki.ubuntu-br.org/RodrigoLima/Cedilha](http://wiki.ubuntu-br.org/RodrigoLima/Cedilha). However, these hacks don't always work nicely, with some applications being left out and worse, they are overwritten at every Ubuntu update.

I can (not happily) redo it every 6 months, but my mother and girlfriend complaining once again about the same issue is not a nice reminder for the Ubuntu update.

Is there any way to make this configuration permanent?

Or, is it possible to the main distribution to have something like a pre-configured "US-International (Dead-key Cedilla)" keyboard layout?

---

### Post by CatKiller on 2011-09-29
Why don't you just use Compose , c? Makes much more sense than using an apostrophe and you don't need to hold any keys down.

Not at my computer so I can't look at keyboard layouts for you. It might be possible to amend one and submit it upstream. You'd probably want to get in touch with the Brazilian localisation people to get it included in future releases. They won't read this post.

---

### Post by CatKiller on 2011-09-29
Double post.

---

### Post by aylons on 2011-09-29
You mean, turning comma a dead-key?

I see what you meant: ", c" looks logical, as comma looks like an upside-down acute diacritic, but it would also mean that every time I want to write a comma I would have to press space before it is being posted. The cure would be worse than the disease.

Moreover "' c " is how we are used to type in Brazil - it's been this way since the first PCs arrived here.

BTW, what I was asking was not about pressing ' and C together, but one after another - the dead-key approach (dead because the first character won't show until the next key is pressed).

Thanks for pointing out Brazilian localization, I will talk to them.

---

### Post by CatKiller on 2011-09-30
No, not a dead key. That always seems like a clunky approach to me. The Compose key is much more elegant. You can set it to whatever you want (I use the right Windows key since it's no use for anything else) and use it to generate characters in a fairly intuitive way. For example, ñ is Compose -> n ->~, which makes a lot of sense to me. As well as being an elegant way of generating characters, it works system-wide and means that you won't need to mess around with things with each release.

---

### Post by aylons on 2011-09-30
I know compose makes perfect sense.... but so does a keyboard in alphabetic order.

However, for the same reason Ubuntu supports QWERTY, it should support cedilla with a dead key: people are used to it and  feel comfortable with it.

-

Moreover, striking 3 keys for a common character is annoying. I don't know if this is your case, but I already noticed  native english speakers tend to underestimate the importance of writing diacritics fast in a fast and comfortable way.

I can see why this happens, as we usually don't care spending a few seconds using two hands for typing a uncommon symbol such as ©, but this is not the case for "ç" in Portuguese.

---

### Post by sanderd17 on 2011-09-30
You can make a custom keyboard layout (if you only need to change one character, it will be quite easy). Just search in your current layout file for the char &#263; and replace it by ç (I assume you don't use the first char).

[http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html](http://hektor.umcs.lublin.pl/~mikosmul/computing/articles/custom-keyboard-layouts-xkb.html)

This will also be overwritten on an Ubunu update, but if you remember to backup the file before you upgrade, you can just restore it (not much work). Also, do backup the original file, you don't want to be left without a keyboard.

I prefer ALTGR+KEY for special characters.

---

### Post by CatKiller on 2011-09-30
Still not at my computer, so still can't test keyboard layouts for you. You don't need two hands to use the Compose key; you don't need more than one finger.

You don't want to re-do your configuration each release, which means you need to use something out-of-the-box. Your preferred solution - a keyboard layout specifically for Brazilian users that behaves the way you want - is going to take some time. (Have you filed a bug report yet?) In the meantime, using the Compose key is quick and painless and gets you easy access to a bunch of other characters for free.

Not that high a proportion of people here are going to experience your problem; this is explicitly an English-speaking forum. There are others for other languages, which may or may not have already solved this problem. At least as many people that use your key combination are going to want the current behaviour rather than the behaviour you want. There are languages besides English and Portuguese and any keyboard layout that calls itself International is going to have to cater to those too.

And I still think using an apostrophe to indicate a mark that goes beneath the line is just weird :)

---

### Post by sanderd17 on 2011-10-01
I use the altgr alternative international layout, mainly for English and Dutch, but occasionally also for German and French. 

And I like it the way it is, except for one thing. In Belgium, an AZERTY keyboard layout is the most common, and the only thing I miss from that layout is the row of numeric keys. In AZERTY, you had to push shift to get a number and pressing the key without shift gave you a symbol. Since my keyboard also has a numpad, I always use that top row for symbols, so I change the behaviour back to the AZERTY behaviour.

---

### Post by leandromartinez98 on 2011-11-30
Please sign out to this bug:

[https://bugs.launchpad.net/ubuntu/+bug/898419](https://bugs.launchpad.net/ubuntu/+bug/898419)

---

### Post by polt on 2012-02-19
Why not just install the Brazil keyboard layout?  It matches the US keyboard almost exactly, except that ; is replaced with c-cedille, so you dont have to type any extra keys to put in the special c.

---

### Post by eudemus on 2012-10-03
In the UK International (with dead keys) keyboard layout, the dead key for cedilla appears to be AltGr + ¨=¨

So, AltGr + ¨=¨ then c gives ç, and it works for capital C too: Ç

I've been spending too many sad hours trying to figure this out.

(one caution, but hopefully not a fly in the ointment, is that I'm running Fedora 17 not Ubuntu just now, but I'd be amazed if it was different for different distros).

Enjoy.

---

