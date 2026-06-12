---
title: "Texmaker vrsion package problem"
date: 2012-04-23
forum: General Help
---

### Post by pesha on 2012-04-23
Hi,

I just ran into a problem creating a document in Texmaker. I decided to  use built-in package vrsion for automatic versioning of my document. The  first time I built my document, everything was OK. Unfortunately, the  next time the vrsion package threw out an error on line 92 of  vrsion.sty:
  
! Missing number, treated as zero.

Anyone ran into this problem before, any known workaround how to fix  this? I tried to reinstall package texlive-latex-extra but that didn't  help. Haven't really been successful googling it either.

Thanks, any help would be appreciated,

Jan

Edit: The first time I run it, vrsion produces file called _document_.vrs with correct version number (one) in the same dir as my document is.

---

### Post by jazzwhiz on 2013-02-27
I also have a problem with vrsion. In particular vrsion seems to clash with revtex 4.1 which I use for writing papers to submit to physics journals. I don't know if that was OP's problem or not. vrsion does work in a minimal example using regular ol' article [and probably other document classes as well] so I know it's not totally busted. It also seems to generate a correct .vrs file even with revtex.

The email address provided with the vrsion documentation is dead. If anyone knows the contact information of Mats Dahlgren its creator it would be much appreciated.

---

