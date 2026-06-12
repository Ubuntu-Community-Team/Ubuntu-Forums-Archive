---
title: "where is pygame/repositories/preinstalled?"
date: 2009-07-17
forum: General Help
---

### Post by bodyharvester on 2009-07-17
wasnt sure where to put this, not really a programmer question,

i have used python and want to get pygame but where is it? the site said it is already in most debian packages (ver1.7)

is it already in my ubuntu 9.04 netbook remix? the repositories or should i download from the site?


thanks

---

### Post by LightningCrash on 2009-07-17
dpkg -l python-pygame
dpkg -L python-pygame

(if not installed:)
sudo apt-get install python-pygame

---

### Post by bodyharvester on 2009-07-17
> **LightningCrash said:**
> dpkg -l python-pygame
dpkg -L python-pygame

(if not installed:)
sudo apt-get install python-pygame

thanks

---

### Post by LightningCrash on 2009-07-17
If you need any help with pygame, I know a little bit about it. PMed you my IM details.

---

### Post by bodyharvester on 2009-07-17
joseph@joseph-laptop:~$ dpkg -l python-pygame
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
ii  python-pygame             1.8.1release-0ubuntu2     SDL bindings for games development in Python

how do i install it?

---

### Post by bodyharvester on 2009-07-17
nevermind, i import it ito python  ;)

---

