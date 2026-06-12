---
title: "command*not*found*-*terminal*not*parsing*spaces?"
date: 2009-11-04
forum: General Help
---

### Post by praxis_guy on 2009-11-04
Ok.***I*upgraded*to*9.10*recently,*but*found*a*problem*whenever*I*tried*to*do*anything*in*the*terminal.**It*took*me*forever*to*figure*out*why*the*terminal*was*sometimes*working*and*sometimes*not.**Now*I*need*to*figure*out*why...

i*can*enter*a*single*word*command.*eg.*"putty"*no*problem.**command*will*execute.

if*i*enter*"putty*192.168.1.1"*for*instance*i*get*the*response*"putty*192.168.1.1:*command*not*found".**For*that*matter*"cd*.."*will*not*work!***Needless*to*say*it's*hard*to*get*anything*done.

it*appears*that*the*command*terminal*does*not*recognise*or*is*unable*to*parse*spaces.**I'm*guessing*here*-*but*it*looks*like*it's*trying*to*run*whatever*i*type*as*a*singe*command.**Am*I*sending*a*bad*character*with*the*space*bar?**i've*tried*xterm*and*have*the*same*problem,*but*all*other*programs*seem*to*work*ok*(i.e.*normally*vis.*using*spaces).**How*do*I*diagnose*without*a*working*terminal?

Please*help.**Thanks*in*advance.

PG

---

### Post by praxis_guy on 2009-11-04
Ha!**Posting*the*messag*seems*to*have*shown*me*the*problem.**Still*don't*know*what's*going*on*though.**Anyone*seen*anything*like*this*before?**Everything*looks*ok*on*my*end,*but*it*looks*like*<space>=*

PG

---

### Post by soapBAR2 on 2009-11-04
It's possible your space key is bound to something bad. Here's a quick fix

```
sudo apt-get install x11-xserver-utils ; sudo xmodmap -e "keycode 65=space"
```

I haven't the guts to try it out for fear of messing up my space bar, but you can't really do any worse than you already are. If this persists on restart/logout, add this script to your autostart (remembering to chmod +x it!)

> #!/bin/bash
sudo xmodmap -e "keycode 65=space"

---

### Post by 3rdalbum on 2009-11-04
I thought you were putting in the asterisks for effect :-)

Are you sure your keyboard is set to the correct layout?

---

