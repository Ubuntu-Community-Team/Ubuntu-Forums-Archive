---
title: "8bit characters: compose / bash"
date: 2006-06-16
forum: General Help
---

### Post by Ulrich Scholz on 2006-06-16
Hi everybody,

I'd like to use German umlauts (e.g., http: &uuml;).  

(1) On other systems, I use a compose character to enter them via,e.g., <compose character> " u.

The compose character is defined in .Xmodmap by 
--
!! Third example: Change right Control key to Compose key.
!! To do Compose Character, press this key and afterwards two
!! characters (e.g. `a' and `^' to get <E2>).
remove  Control  = Control_R
keysym Control_R = Multi_key
add     Control  = Control_R
--

This (i.e., xmodmap .Xmodmap) doesn't work anymore under kubuntu 6.06.

(2) On said other systems, bash shows umlauts.  On kubuntu 6.06 it does not, see the attached png.  How can I see them correctly?

Thank you, Ulrich

PS. I'm not sure this is the right forum for this kind of question.  If not, which is it?

---

### Post by steve.horsley on 2006-06-16
Just a wild thought - perhaps your chosen font doesn't have those characters - try changing to a unicode font.

---

