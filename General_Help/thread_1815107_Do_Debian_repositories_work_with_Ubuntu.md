---
title: "Do Debian repositories work with Ubuntu?"
date: 2011-07-30
forum: General Help
---

### Post by teh5abiking on 2011-07-30
Well considering the fact that Debian and Ubuntu are tightly knit together, I wanna know if I can use a Debian repository on Ubuntu 10.04. 

I migrated from Wheezy to Lucid since I was having a lot of driver errors. But I'm missing some stuff that are in Debian's mirrors that aren't in Ubuntu's repositories that I make use of quite often (a few IDEs and a couple of compiler scripts that i use for my android-related business) 

So far, I can find the deb packages, but i can't install them because they're missing dependencies and stuff. 

Can I add Debian repos to Ubuntu 10.04, or should I look somewhere else?

---

### Post by cbowman57 on 2011-07-30
Yes you can.

---

### Post by jerrrys on 2011-07-30
never done that, but

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+Debian+repos&as_qdr=all&sa=Google+Search&lang=en#926](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+Debian+repos&as_qdr=all&sa=Google+Search&lang=en#926)

---

### Post by Morbius1 on 2011-07-30
According to the source of all knowledge in the known universe the answer appears to be no.

[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)
> Ubuntu is a fork of the Debian project's codebase.

Debian and Ubuntu packages are not necessarily binary compatible with each other, however, and sometimes .deb packages may need to be rebuilt from source to be used in UbuntuFrom a practical sense however I don't know - never tried it.

---

### Post by cbowman57 on 2011-07-30
I've done it, I think it goes without saying that it could cause problems though.

---

### Post by bodhi.zazen on 2011-07-30
Well, first, in general there is no need to.

Second, it depends , which version of Ubuntu and which debian repo ?

You can try it with pinning

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

But you will need to understand what you are doing and be prepared to fix a very broken system.

So I would say, if you have to ask, don't do it unless you are willing to break your system.

You are far better off installing from source then mixing repos.

What is it you are trying to install and what makes you think you want to use the Debian repos ?

---

### Post by ssokolow on 2011-12-21
> **bodhi.zazen said:**
> 
What is it you are trying to install and what makes you think you want to use the Debian repos ?

I'm not sure what he was trying to install, but I was thinking of it because, in Oneiric, okular-extra-backends doesn't provide CHM support but the Debian build of the same package does and, unlike in Gentoo, I have no clue how to play with compile flags in Ubuntu.

---

### Post by bodhi.zazen on 2011-12-21
> **ssokolow said:**
> I'm not sure what he was trying to install, but I was thinking of it because, in Oneiric, okular-extra-backends doesn't provide CHM support but the Debian build of the same package does and, unlike in Gentoo, I have no clue how to play with compile flags in Ubuntu.

Most of the gentoo compile flags are either options for gcc, options for ./configure, or environmental variables.

But, no there is no central configuration file in Ubuntu (or any binary distro) similar to gentoo (source distro).

---

