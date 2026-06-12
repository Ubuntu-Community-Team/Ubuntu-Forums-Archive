---
title: "What is conky?"
date: 2011-03-29
forum: General Help
---

### Post by galacticaboy on 2011-03-29
I have heard people talk about conky, what is it?

---

### Post by WorMzy on 2011-03-29
A system monitor for X originally based on the torsmo code, but more kickass. It just keeps on given'er. Yeah.

([link]("http://conky.sourceforge.net/docs.html"))

---

### Post by completist on 2011-03-29
Conky is a great tool.  Here is a link to conky configs and screens.

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by galacticaboy on 2011-03-29
> **WorMzy said:**
> A system monitor for X originally based on the torsmo code, but more kickass. It just keeps on given'er. Yeah.

([link]("http://conky.sourceforge.net/docs.html"))

How do I install it? That link is a little advanced for me, I did sudo apt-get install conky but I cannot find it.

---

### Post by Vaphell on 2011-03-29
it's not in menus, you have to run it from command line, just type conky in terminal

for starters copy-paste some example config from the link in #3 and save it as .conkyrc in your home dir. when you run conky it will pick up the config and draw stuff accordingly. Then you can tweak that config file to your liking.

put a simple script in autostart that has the following
sleep 20 && conky
conky for some reason requires that initial delay when user session loads (number of seconds in sleep is not set in stone, tweak to suit your needs)

---

### Post by stinkeye on 2011-03-30
[**_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")

---

