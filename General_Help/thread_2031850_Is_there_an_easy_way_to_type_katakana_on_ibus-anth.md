---
title: "Is there an easy way to type katakana on ibus-anthy?"
date: 2012-07-22
forum: General Help
---

### Post by Sandertje on 2012-07-22
Hi people,

Does anyone know if there is an easy way to type katakana on ibus-anthy? Right now, I only find to be able to type katakana by basically going through the kanji list after typing a hiragana character, by hitting space a number of times. That gets quite tedious if you want to type a rather lengthy long string of katakana characters (for instance, something like &#12511;&#12517;&#12540;&#12472;&#12483;&#12463;&#12471;&#12540;&#12531;). I do notice that anthy sorta "learns" what I want to type by placing the katakana characters higher up the kanji list. Is there any key i'm missing that enables me to type only katakana for a while, before reverting back to hiragana? 

I am using Ubuntu 12.04 LTS. 

Thanks!

---

### Post by mirzahadi on 2012-07-25
I am having the same problem. Apparenty Ctrl+ should cycle between three modes of input;Hiragana, Katakana and the half Hiragana or something like that. But it doesn't work.

F7 is working for me which changes all the selected Hiragana to Katakana. It might also work for you.

I also can't find a way to change the Anthy settings. There used to be an 'i' icon in the bar above in Ubuntu 10.04 when Japanese input was selected but it doesn't show any more. 

I would really appreciate some help.

I am using Ubuntu 11.04.

---

### Post by Sandertje on 2012-07-29
Thanks!

I didn't know about F7. That's working for me :-)
In 12.04 LTS, at least, there's a keyboard logo on the notification bar. You can select anthy there (alternative to cntrl+space), and when that happens, the keyboard becomes an "A" coupled to &#12385;.

---

### Post by aelfwyne on 2012-09-24
Thanks for this, the F7 is useful.

However, like others, I'm wondering why the Preferences button is grayed out. Other (non-Ubuntu) Linuxes have access to the Anthy preferences there. Ubuntu should not be blocking that - what's missing?

There doesn't seem to be a bug filed on Anthy or Ibus for this either, and it seems like a pretty obvious bug to anyone who actually uses input methods.

---

### Post by russomarco on 2013-08-27
[FONT=microsoft sans serif][COLOR=#333333]I know this is a bit old, but I customized the behavior of Anthy by launching the script [/COLOR]**ibus-setup-anthy **[COLOR=#333333]from the [/COLOR]**usr/lib/ibus-anthy**[COLOR=#333333] folder. When selecting the Anthy input method in ibus, the *Preferences* button is grey and can't be used (I don't understand why), but it can still be used in the way I wrote. I hope this helps![/COLOR][/FONT]

---

