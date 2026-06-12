---
title: "Trying to make a custom IME"
date: 2010-10-03
forum: General Help
---

### Post by Veteropinguis on 2010-10-03
I'm trying to make a custom IME, but can't find a good set of instructions. I'm trying to work with SCIM (if there's another way that would be wonderful) but I don't completely understand the instructions I've found.

I've read and attempted to follow [http://www.scim-im.org/development/contribute/how_to_create_a_new_ime_in_about_15_minutes_with_scim_and_scim_tables](http://www.scim-im.org/development/contribute/how_to_create_a_new_ime_in_about_15_minutes_with_scim_and_scim_tables) and [http://lists.freedesktop.org/archives/scim/2004-October/001024.html](http://lists.freedesktop.org/archives/scim/2004-October/001024.html) but with no luck.

When I tried to use SCIM, I tried editing a premade IME, which didn't work. I either got no output, or Latin characters. Making my own file didn't work either.

I'm really at a loss here. Can anyone help?

---

### Post by Veteropinguis on 2010-10-06
Bump.

Bump again.

---

### Post by Veteropinguis on 2010-10-07
Anyone? Any info about IME-making would be greatly appreciated...

---

### Post by Veteropinguis on 2010-10-10
Bump

---

### Post by Veteropinguis on 2010-10-11
Seriously, any sort of good newbie guides to read about IMEs would be wonderful. What I've managed to find on my own has required too much technical knowledge.

If anyone knows anything, please share. :popcorn:

---

### Post by kumaryu on 2010-10-11
What language/character-set is it for?

---

### Post by Veteropinguis on 2010-10-26
It's for hieroglyphs.

---

### Post by kumaryu on 2010-10-27
I know very little about IME programming, or for that matter, writing systems but some notes and observations..

1. Since Karmic (9.10), Ubuntu has standardised on IBus instead of SCIM as an imput method framework for CJK and other languages. The project page is here:
 [http://code.google.com/p/ibus/](http://code.google.com/p/ibus/)
 [http://code.google.com/p/ibus/wiki/HowToCreateATableForIBusTable](http://code.google.com/p/ibus/wiki/HowToCreateATableForIBusTable)
It may be easier to choose IBus as the framework since it would work with the least effort in the current/future versions of Ubuntu and more current references would be available.

2. The most common IMEs for use with CJK languages in IBus are respectively; Chewing: Chinese, Anthy: Japanese and Hangul: Korean. With regard to the three writing systems, the following generalisations may be made:
  Chinese: logographic
  Japanese: mixture of logographic and syllabic
  Korean: featural/syllabic

3. These differences between the writing systems have resulted in the development of distinct input mechanisms particular to each writing system:

a. In Chinese Pinyin method (used in Chewing) phonetic pronunciations are typed on the kleyboard and the IME offers a list of candidate character(s).

b. In Korean (Hangul),the initial "jamo" (component of the syllabic character) is keyed in and the subsequent  components are created on the fly by the IME until the character is complete.

c. In Japanese (Anthy), the phonetic inputs are translated into appropriate syllabic characters "kana" on the fly. The resulting composites are highlighted for further transformation into "kanji" characters as and when required. To each selected "kana" groupings the IME offers a list of candidate character(s).

---

### Post by kumaryu on 2010-10-27
4. There is another method for Chinese input, "Cangjie" which utilises the basic character components (24 radicals and associated auxiliary shapes) that compose the characters. This is based on the fact that many of the characters are compound characters made up of more than one. This however requires the mapping of the basic radicals to the keyboard.

I listed the characteristics of the various writing systems and the input methods used because I suspect that one of them may already be suitable as a mechanism for hieroglyphs with the least amount of additional work. One possibility along this line of reasoning would be to use IBus-tables; 
 [http://code.google.com/p/ibus/wiki/TableReadme](http://code.google.com/p/ibus/wiki/TableReadme) <English description at the bottom>
to input phonetic equivalents (or words) to which the IME would respond by presenting a list of glyphs that corresponds to the sound (or the meaning) for the user to choose from.

---

