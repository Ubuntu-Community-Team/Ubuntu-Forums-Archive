---
title: "Installing a new LaTeX class and importing it to LyX"
date: 2010-06-12
forum: General Help
---

### Post by nandugopan on 2010-06-12
Guys,

I am totally new to LaTeX. I need to prepare a journal paper regarding my project work. I have some experience in preparing articles using LyX. The Elsevier group of journals has a format which is available as a zip file  from [http://www.elsevier.com/framework_authors/misc/elsarticle.zip](http://www.elsevier.com/framework_authors/misc/elsarticle.zip)

Could anyone help me out as to how to install this in a LaTeX environment like Kile?

Is it possible to import this to an environment like LyX?

Hoping to hear from you,

Nandu

---

### Post by Stefan_K on 2010-06-28
Hi Nandu,

you just need to extract the package in your TeX tree and run texhash or [mktexlsr]("http://texblog.net/hypertext-help/latex-tools/mktexlsr/"):
```
sudo texhash
```
Or put it to below your home directory: ~/texmf.

Stefan

---

### Post by nandugopan on 2010-07-14
Thanks Stefan...
That did the trick..Things seem to be fine now...:KS

---

