---
title: "Flash problems"
date: 2009-07-26
forum: General Help
---

### Post by felinoel on 2009-07-26
I use FireFox, and am unsure how to explain this... when I come across something involving Flash... it mildly works? Sometimes it has this gray play button over it that I have to click to get it to play (don't want that), sometimes it just works fine, and sometimes it gets this gray screen with lines shooting through it?

It worked fine for me before, but I reinstalled Ubuntu and now it isn't working too well?

---

### Post by SoMBS on 2009-07-26
I had a few issues with Flash when first going to 9.04. After some Googling I tried a sequence of steps that have worked to correct some of the issues.

1.Remove .mozilla from home folder e.g., /home/yourhome/.mozilla
2.Then remove Flash using Synaptic
3.Then remove Firefox using Synaptic
4.Now reinstall Firefox using Synaptic
5.Then install Adobe Flash using Synaptic

HTH

---

### Post by felinoel on 2009-07-26
This will remove some bookmarks won't it... ok, will try that

---

### Post by felinoel on 2009-07-26
I went to remove Flash using Synaptic, but I am not entirely sure what I am looking to remove?

---

### Post by bcschmerker on 2009-07-26
> **felinoel said:**
> I went to remove Flash using Synaptic, but I am not entirely sure what I am looking to remove?If I may interject, Adobe Laboratories Flash Player may be in one of two Debian package families:

(1) flashplugin-nonfree
(2) adobe-flashplugin

Either but not both will be listed in Synaptic under Status: Installed, as adobe-flashplugin conflicts with/replaces flashplugin-nonfree.

---

### Post by felinoel on 2009-07-26
> **bcschmerker said:**
> If I may interject, Adobe Laboratories Flash Player may be in one of two Debian package families:

(1) flashplugin-nonfree
(2) adobe-flashplugin

Either but not both will be listed in Synaptic under Status: Installed, as adobe-flashplugin conflicts with/replaces flashplugin-nonfree.

You may indeed

---

### Post by felinoel on 2009-07-26
I see flashplugin-nonfree, bt it is not installed... should I install it? Or should I ignore it and continue down the checklist?

---

### Post by R.Bucky on 2009-07-26
Take a look at this informational post ([http://buckycomputing.net/blog/downgrade-flash-10-for-wordpress/](http://buckycomputing.net/blog/downgrade-flash-10-for-wordpress/)). When Adobe upgraded from Flash 9 to 10, they lost some functionality. It may be your problem.

---

