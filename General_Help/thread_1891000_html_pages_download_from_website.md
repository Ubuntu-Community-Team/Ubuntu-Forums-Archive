---
title: "html pages download from website"
date: 2011-12-04
forum: General Help
---

### Post by coffeecake on 2011-12-04
does anyone know of a good website copier that runs on ubuntu and that downloads and saves html files so that i can open them without the need of the original program.

---

### Post by idoitprone on 2011-12-04
If you just want to download the html text code then I guess on command line

```
wget -r [url]
```example
```
wget -r google.com
```Website are built differently, depending on the website, they might thwart you efforts.

All html code can be opened by any webbrowser

---

### Post by coffeecake on 2011-12-05
> **idoitprone said:**
> If you just want to download the html text code then I guess on command line

```
wget -r [url]
```example
```
wget -r google.com
```Website are built differently, depending on the website, they might thwart you efforts.

All html code can be opened by any webbrowser

I mean i want to download at least a small part of a website. I only know the homapage url. So with wget i may not be able to solve my problem.

---

### Post by aeiah on 2011-12-05
if you don't know the location of the data, how will your software?

wget can open links recursively, and you can specify recursion depth, but if there are no links on the front page and no way to figure out where the content is, you wont get very far

---

### Post by coffeecake on 2011-12-05
> **aeiah said:**
> if you don't know the location of the data, how will your software?

wget can open links recursively, and you can specify recursion depth, but if there are no links on the front page and no way to figure out where the content is, you wont get very far

Could you please tell me how to make wget recursively download html pages ?

---

### Post by Lars Noodén on 2011-12-05
> **coffeecake said:**
> Could you please tell me how to make wget recursively download html pages ?

It's described above in post [#2](http://ubuntuforums.org/showpost.php?p=11513454&postcount=2).  It is done with the help of the **-r** or **--recursive** [option](http://manpages.ubuntu.com/manpages/precise/en/man1/wget.1.html).  Other options like --no-parent, --convert-links and --page-requisites might be useful to look at, too.

---

