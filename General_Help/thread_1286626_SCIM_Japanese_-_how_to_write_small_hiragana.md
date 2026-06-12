---
title: "SCIM Japanese - how to write small hiragana?"
date: 2009-10-09
forum: General Help
---

### Post by tripler on 2009-10-09
I've got Ubuntu 9.04 and I'm using SCIM to write Japanese. It works fine but I can't find a way to type a small hiragana. It has "Half width katakana" in the list, which types a small katakana. 

Anyone know how to do it?

---

### Post by guriinii on 2009-10-09
For what do you need half width hiragana? Their is only one half width character in that alphabet, which is a small *tsu* &#12387;, that indicates that the following consonant is doubled. For example &#12373;&#12387;&#12363; sakka 'author'. 
Anthy automatically recognises this and corrects it. Therefore there is no half width option in Anthy.

Hope this helps.

---

### Post by tripler on 2009-10-09
I've found any key which doesn't represent another hiragana if pressed twice gives &#12387;. eg. tsu = &#12388;, mm = &#12387;. Works the same for katakana. But how can I get a small &#12420;, &#12422; and &#12424;? If I type &#12366;&#12422;&#12358;&#12395;&#12422;&#12358; ("milk" but &#12422; should both be small) and hit space it gives &#32681;&#12422;&#40284;&#12395;&#22805;, which doesn't make any sense. I've got muti-segment on in Anthy. It doesn't work any better with single-segment. 

While I'm on the subject, is there a shortcut key to change between hiragana and katakana?

---

### Post by tripler on 2009-10-09
For anyone else who needs small hiragana, do this:

Click on the "Show command menu" on the SCIM box (it's a page icon next to the question mark), go to SCIM Setup/Anthy/Romaji typing/Customize and you'll see the keys for small hiragana in the list. They can all be written small but the common ones follow this pattern:
kya = &#12365;&#12419;, kyu = &#12365;&#12421;, kyo = &#12365;&#12423;

Still looking for a way to switch between hiragana and katakana via the keyboard.

---

### Post by martelo on 2011-04-10
I am using uim with m17n, and for me, the letter x seems to work for small hiragana, e.g., xa would give &#12353;.  I don't know if it is the same on scim or not.

---

