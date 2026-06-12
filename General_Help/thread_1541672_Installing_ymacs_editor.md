---
title: "Installing ymacs editor"
date: 2010-07-29
forum: General Help
---

### Post by David Vincent-Jones on 2010-07-29
I am trying to install the YMACS editor for chrome.

The source file (ymacs-latest.tar.gz) contains no 'read-me' or other instructions.

I would appreciate help from others in getting this installed.

---

### Post by dino99 on 2010-07-29
the home page

[http://www.codeproject.com/News/12963/Ymacs.aspx](http://www.codeproject.com/News/12963/Ymacs.aspx)

---

### Post by David Vincent-Jones on 2010-07-29
Thanks ... I have seen this page but I do not find any instructions for installing the tar.gz file.

I see no signs of a make or configure files or other assistance in the package.

---

### Post by anubhavrocks on 2010-07-29
build/build.sh

---

### Post by dino99 on 2010-07-29
you can use alien to make installation via a deb file:

sudo apt-get install alien gdebi

goto ymacs-latest.tar.gz place ( cd ...)

sudo alien -k ymacs-latest.tar.gz

you got a deb now , double click on it, that it:p

---

### Post by David Vincent-Jones on 2010-07-29
Thank you ... that was useful

---

### Post by dino99 on 2010-07-29
hey, ive learn myself :p with a nice friend of mine: google ;)

---

