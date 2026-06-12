---
title: "certain fonts cause greek letters to appear as symbols"
date: 2010-09-12
forum: General Help
---

### Post by chriskin on 2010-09-12
well , some fonts cause some greek letters to appear as squares or symbols - while the rest appear correctly.

is there any way to make all non-latin characters to use a font different than the one the latin characters use?

---

### Post by simosx on 2010-09-24
You need to give some more details, such as which program/fonts you are using.

In general your main font is used to represent characters for Greek in applications. If you made a weird change in your Font preferences to a font that does not have the full Greek repertoire, then your system will try to use other existing fonts to make up the missing Greek characters.

---

### Post by chriskin on 2010-09-25
> **simosx said:**
> You need to give some more details, such as which program/fonts you are using.

In general your main font is used to represent characters for Greek in applications. If you made a weird change in your Font preferences to a font that does not have the full Greek repertoire, then your system will try to use other existing fonts to make up the missing Greek characters.

what i wanted to know is if i can choose which font the system will use to make up for the missing characters

---

### Post by Odys1 on 2012-08-07
I experience the same problem too. I transferred some text files from a microsoft system to ubuntu, and the characters appeared in cyrillic symbols! I thought that the problem was the missing lucida console font, which is Notepad's default font. Nothing changed after the installation of that font, so I suspect the problem lies in the character encoding. The default character encoding of the nautilus file manager in Ubuntu 12.04 is UTF-8 and after a brief search in google I found that that it might help if we change nautilus's encoding to iso-8859-7. I will keep you updated if I find a solution.

---

