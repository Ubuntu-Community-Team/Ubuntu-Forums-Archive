---
title: "Help: can't exit MAN pages"
date: 2005-02-09
forum: General Help
---

### Post by sagara on 2005-02-09
This more of a UNIX related question.

I dont know why but after I run man on my terminal, i cant exit it using CTRL + C.
So basically I loose the terminal.

What is wrong?

---

### Post by Wim Sturkenboom on 2005-02-10
The official way to leave *man* is the same as in *vi*. Type a colon to go to a command line and press **q** (for Quit).
You can also search in man pages. Instead of a colon, use a slash and enter your search. This is case sensitive.

PS just found that a q without the colon also works

---

### Post by apoc on 2005-02-10
Ctrl Z works aswell

---

### Post by benjamin on 2005-02-10
q   works ... for me.

---

### Post by mendicant on 2005-02-10
It actually depends on your setting of PAGER and the setting of /etc/alternatives/pager.  I think by default, /usr/bin/pager is less, but you can change the pager used

% PAGER="" man man ## the man page prints on the terminal very quickly
% PAGER=more man man ## the man page prints using more
% PAGER=cat man man ## same as PAGER=""
% man -Pmore man ## also sets the pager to use
% man --pager=more ## also sets the pager to use

So, by default, all the commands that less uses can be used when viewing man pages.

---

### Post by -Rick- on 2005-02-10
[QUOTE=apoc]Ctrl Z works aswell[/QUOTE]
Actually that won't quit man, but just put it in the background(type fg to activate it again).

---

### Post by Jad on 2005-02-10
: then q

---

### Post by mendicant on 2005-02-10
So, from the man page for less:

       q or Q or :q or :Q or ZZ
              Exits less.

---

