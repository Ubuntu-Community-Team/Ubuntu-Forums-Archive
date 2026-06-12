---
title: "using extended ascii characters on Ubuntu"
date: 2009-12-14
forum: General Help
---

### Post by groundnut on 2009-12-14
Today I tried to use extended ascii characters (e.g.: alt 130 in Windows) while writing an email in Gmail. It did not work.

How can I use these extended ascii characters in Ubuntu?

---

### Post by StuartN on 2009-12-14
> **groundnut said:**
> How can I use these extended ascii characters in Ubuntu?

Linux has many comprehensive (and internationally standard) ways of entering characters. The extended ascii character 130 seems to be e-acute and can be obtained as an accented character using the compose key, compose-'-e -> é. It is also the unicode character 00E9 and can be obtained as ctrl-shift-u-00E9. Both produce the same code.

There is more about the compose key here [https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

and a Unicode lookup here [http://www.unicode.org/charts/charindex.html](http://www.unicode.org/charts/charindex.html)

---

### Post by groundnut on 2009-12-14
Thanks StuartN,

The e-acute was just an example. I have now learned to type this symbol with AltGr - e.

Is there no way to use the extended ascii code alternatively to unicode?

---

### Post by StuartN on 2009-12-14
> **groundnut said:**
> Is there no way to use the extended ascii code alternatively to unicode?

You will have to either use the accents through compose, or find the Unicode equivalents. It is a universal system that all modern software is adopting, and much more consistent and versatile than the old codepages.

You may find Applications->Accesories->Character Map useful, but you might find that switching to View->By Unicode Block is helpful. You will see all the available characters, which you can copy individually, or make a string to copy, or read off the Unicode value.

---

### Post by groundnut on 2009-12-15
Thanks again StuartN!

That Character Map is great. All I need.

---

