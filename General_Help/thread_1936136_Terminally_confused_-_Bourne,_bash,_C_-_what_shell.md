---
title: "Terminally confused - Bourne, bash, C - what shell is Gnome default?"
date: 2012-03-05
forum: General Help
---

### Post by mbuell on 2012-03-05
Just a simple question - a search turns up so much stuff it would take a year to sort through it!

What is the default shell in Gnome 2 / Ubuntu 10.04?  Is it different for Gnome 3 or Unity?

Maybe, to make it clearer - let me tell you why I ask. I have installed the Oracle XE database - and it has two scripts I have to choose from, based on my shell. One script is for "Bourne, Bash, or Korn shell". The other is for "for C or tcsh shell". I read that BASH is the default Linux shell - but since the Gnome terminal is written in C, I am terminally confused. 

Would anybody care to tell me which is what?

---

### Post by idoitprone on 2012-03-05
use borne shell it is also called bash. it the shell that everyone uses. All other shell except for dash came before it. Dash is ubuntu default shell; however, the scripts must be posfix unlike bash. Gnome's default should be bash.

---

### Post by ratcheer on 2012-03-05
No, Bourne shell is NOT also called bash. The Bourne shell is sh, the Bourne Again shell is bash.

And, to answer the original question, **bash** is the standard shell of Ubuntu (and most Linuxes).

Tim

---

### Post by idoitprone on 2012-03-05
> **ratcheer said:**
> No, Bourne shell is NOT also called bash. The Bourne shell is sh, the Bourne Again shell is bash.

And, to answer the original question, bash is the standard shell of Ubuntu (and most Linuxes).

Tim
  crp i made an newbie error opps

I wonder if the defaul is bash in ubuntu because when the user put
#!/bin/sh

dash will interpret the script in debian and ubuntu.
[https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

---

### Post by ratcheer on 2012-03-05
Yes, bash is the default shell. If you put #! and a path to another shell, it forces that other shell to be used. You could use any other shell you have installed on your system.

Tim

---

### Post by HiImTye on 2012-03-05
always use '#!/bin/bash' because, well, if you have a powerful shell like bash, why wouldn't you?

---

### Post by mbuell on 2012-03-05
> **ratcheer said:**
>  . . .to answer the original question, **bash** is the standard shell of Ubuntu (and most Linuxes).

Tim

Thank you, thank you. That is exactly what I was seeking to know. 

I have no intention of exploring different shells - if bash is default, it is default for some reason. And, since I do not even approach using it to any sort of limitation - I do not wish to spend time exploring!

---

### Post by Khayyam on 2012-03-05
> **mbuell said:**
> [...] I have no intention of exploring different shells - if bash is default, it is default for some reason. And, since I do not even approach using it to any sort of limitation - I do not wish to spend time exploring!

Its the default because its part of GNU and so became the standard shell with most Linux distributions. If another shell of the 'bourne' family (zsh, or ksh) were to be set as your default shell you probably wouldn't notice the difference. In terms of scripting bash and zsh are just about interchangable (both being 'bourne' derivitives), its mostly interactive features that govern peoples choice of one over the other.

best ... khay

---

### Post by sisco311 on 2012-03-06
BASH is considered to be the *de facto* shell, while sh ( the Bourne shell ) is considered to be the *de jure* one.

the law: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)
a bash guide: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

