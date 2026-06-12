---
title: "Compiling package?"
date: 2010-02-08
forum: General Help
---

### Post by jprophet420 on 2010-02-08
I am currently trying to compile some apps and I remember that there was a "sudo apt-get install X" that installs all the packages I'll need to compile. The first one is flex, second is bison etc etc. I dont feel like trying to compile over and over and each time that I get a little farther have to install a new package. Thanks.

---

### Post by Leppie on 2010-02-08
it will be difficult to install ***all*** packages required for compilation of ***any*** package.
some you will have to compile using one language and others will require other languages. some packages require some other -dev packages to be installed, others may compile just like that.
the most generic package required for compiling is build-essential though:
```
sudo apt-get install build-essential
```

---

### Post by jprophet420 on 2010-02-08
Specifically I am trying to compile wine and it needs X support. However I think this install is broken as it is an upgrade and when I try to install with a package it gives a broken package error.

I installed build-essential, automake, flex, bison, and x-dev.

And really thats all thats on here. It was a fresh 9.04 install with 9.10 upgrade.

---

### Post by Leppie on 2010-02-08
have you tried resolving the broken package issue first?
```
sudo apt-get install -f
```

alternatively, you may want to check the "broken packages" section under "custom filters" in synaptic.

---

### Post by texaswriter on 2010-02-08
Hi guys, call me a nerd, 

but I read the Debian notes for Lenny. Especially for new versions of Debian and hence Debian based distro's. 

using ```
aptitude
``` is more robust than ```
apt-get
```. If you want to know a difference [and I haven't tested this on Ubuntu], try installing a few programs that install prerequisites. Then remove them. Apt-get will fail [a surprising amount of times] to uninstall those dependencies. Aptitude will never fail to remove rogue packages. I tried using apt-get once in Sidux, but it left SO MANY stranded packages, I had to apt-get install aptitude... 

So, I did want to note that you should always use aptitude and not apt-get... 

I'm going to put this in my signature so I don't have to note it everytime I see that. I see that **ALOT.  **And there is a **huge** difference between the two. Aptitude is much more powerful. The only thing I use apt-get for is apt-cache... ```
apt-cache search kirby
``` All the apt- commands were separated, but mostly combined into aptitude now... Aptitude search won't search the description, only the title. :popcorn::KS:p;):D

---

### Post by Leppie on 2010-02-08
> **texaswriter said:**
> Aptitude is much more powerful. The only thing I use apt-get for is apt-cache... ```
apt-cache search kirby
``` All the apt- commands were separated, but mostly combined into aptitude now... Aptitude search won't search the description, only the title. :popcorn::KS:p;):D
depends on what you like to use... in ubuntu a lot of users mostly use synaptic...

---

### Post by oldos2er on 2010-02-08
You could try ```
sudo apt-get build-dep wine
```

---

### Post by texaswriter on 2010-02-08
> **Leppie said:**
> depends on what you like to use... in ubuntu a lot of users mostly use synaptic...

I imagine synaptic used apt-get as a backend. I don't know. 

But, if you are going to remove files, at least do it on terminal with aptitude remove...

Seriously, if you apt-get install in a terminal and apt-get remove in a terminal, you would notice fast that apt-get remove leaves ALOT of stuff behind. 

Your system, your choice. 

**FWIW**!!!

---

### Post by Leppie on 2010-02-08
> **texaswriter said:**
> Seriously, if you apt-get install in a terminal and apt-get remove in a terminal, you would notice fast that apt-get remove leaves ALOT of stuff behind.
i hardly ever use apt-get remove... but almost always apt-get purge... if you want to be sure everything is removed, you should always check the dependencies and include them in the remove.

---

