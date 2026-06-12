---
title: "LaTeX package foiltex (aka foils) broken in Lucid"
date: 2010-05-05
forum: General Help
---

### Post by xvila on 2010-05-05
After upgrading from Karmic to Lucid, both in my iMac and my MacBook, I found that LaTeX documents using the "foiltex" package no longer compile

I get all sort of silly errors (like "undefined control sequence \item")

The very same document works fine in my home desktop (still with Karmic)

The workaround:
I completely removed foiltex (apt-get remove --purge foiltex) and installed it from scratch from a source downloaded from CTAN and now things are back to normal

The Problem:
I am not a TeXpert, but it appears to be a problem with the TeX distribution (at least the foiltex package) in Lucid

The optimal solution:
Any ideas ?

Xavi

---

