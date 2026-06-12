---
title: "Specifying Specific Fonts For Specific Languages?"
date: 2011-03-08
forum: General Help
---

### Post by ChipOManiac on 2011-03-08
Hello There!! Thanks For Viewing This Post!!

As a bilingual user, I have a lot of things that someone like that has to have :roll: like a lot of UNIcode fonts of the languages I use and keyboard layouts... etc... etc... :D

My question is really simple (though the answer may not :():

[B]Is it possible to specify a specific font for a specific language?
[/B]
For example:
I have about four different looking Singhalese fonts on my system: LKLUG, Bashitha, Malithi, and... another one... right now my system uses LKLUG, but I'd like to use Bashitha since it's more easy to read. How do I do this? Things like setting the system wide font in SystemSettings or other ways is not what I'm looking for though... my System font is DejaVu Sans, and I want the System to use a specific font when displaying a language.

If it's DE dependent, I'm using KDE 4.4.5

Thanks for any help and criticism :D

---

### Post by ChipOManiac on 2011-03-15
Okay for now I have edited my [FONT="Courier New"]~.fonts.conf[/FONT] to have this addition:
```

<match target="pattern">
   <test name="family" qual="any">
      <string>LKLUG</string>
   </test>
   <edit name="family" mode="assign" binding="same">
      <string>BhashitaComplex</string>
   </edit>
</match>

```

And it works so far with just one glitch, if I do this instead

```

<match target="pattern">
   <test name="lang" qual="any">
      <string>si</string>
   </test>
   <edit name="family" mode="assign" binding="same">
      <string>BhashitaComplex</string>
   </edit>
</match>

```

The fonts of some OTHER languages change drastically and for no reason... any ideas?

Thanks to anyone who tried to help. :D

---

