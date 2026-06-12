---
title: "Using Pari/GP with Ubuntu"
date: 2009-09-04
forum: General Help
---

### Post by sopadeajo on 2009-09-04
I am new to linux and to Ubuntu.I downloaded Pari/gp a free mathematical package calculator and programming language that i used with Vista.
But when i want to start Pari/GP i casnnot find the equivalent (in Linux) of the .exe starting file in windows.
Any possible help?
In other words i want to use Pari/gp with Ubuntu and i do not know how to do it.Seems to be less intuitive to do than with Windows (I had just to double-click on an exe file to start with windows. How to do it with Ubuntu?

---

### Post by egalvan on 2009-09-04
First, doing things "the Windows Way" is "intuitive" because you are used to it.

Second, Window programs do not run directly on Liunx without some help.

Wine is a "program" that allows *some* Windows software to run inside Linux.

The best way is to find an equivalent piece of software that is native to Linux.

Synaptic is your best friend when it comes to looking for software to run under Linux.
Open it up and search for "mathematics", or whatever you like.
Post a message on this forum... describe as detailed as possible what Pari/GP is and does... is there a web-page for it?

And Synaptic is the way to install Wine.

---

### Post by sopadeajo on 2009-09-04
But I have downloaded the linux version of Pari/GP which certainly can be used under Linux (and I suppose so under Ubuntu):
[http://pari.math.u-bordeaux.fr/download.html](http://pari.math.u-bordeaux.fr/download.html)

The problem it is the first time i use Ubuntu (and Linux) and I do not know how to start Pari/GP.With Windows i had to double click on a file called gp.exe and that's all.And with Ubuntu?

---

### Post by sopadeajo on 2009-09-05
Well, the solution was easy: download Pari/gp with Synaptic package manager; open a Terminal window, write gp on it and click enter and Pari/gp starts.
I was expecting a Linux file similar to gp.exe in Windows to be double clicked for starting Pari;  and did not find it. It took me a whole day to find the solution.

---

### Post by roderickf on 2010-04-25
Here is all what u need to do:
```
sudo apt-get instal pari-gp
```
If you have Sagemath installed then just call pari-gp by
```
gp_console()
```
All these installs might not be the latest available on pari-gp official site.

---

