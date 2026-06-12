---
title: "man pages missing?"
date: 2009-12-20
forum: General Help
---

### Post by Cardale on 2009-12-20
I have been following some tutorials and a lot of the man pages they use as examples I can't find using the same commands.

For example man bind gives me nothing.  Do I need to download a package to get more man pages?

---

### Post by FearfulJesuit on 2009-12-20
Your conjecture of downloading additional packages is correct. There are packages in synaptic which are labeled as blah blah-doc. These are the manpages for the program that you download. If you do not have these, then that means the manpages for the program are not installed.

---

### Post by k3lt01 on 2009-12-22
If you want to access Man pages you don't have on your PC you can go [here]("http://manpages.ubuntu.com/")

You can also add the Man pages search engine into FireFox by clicking on the 3rd link down that page.

It's that easy.:popcorn:

---

### Post by geirha on 2009-12-22
bind is a c-function. The man-pages for the standard c-functions are not installed by default. You can install them with the package: [manpages-dev](apt://manpages-dev)

---

