---
title: "restricted Extras"
date: 2010-05-03
forum: General Help
---

### Post by nixIT on 2010-05-03
Hello all,

Installed Lucid over the weekend, ran into a few problems with the alternate install but the liveCD worked like a charm.

While installing all the additional software (java, flash, etc), I ran across [this post]("http://ranjith.zfs.in/ubuntu-10-04-lucid-lynx-post-installation-guide/"), more specifically this line:

> 
Base Note:

Installation only works completely and properly when done from the command-line Terminal. The entire package will not usually install completely from within a Package Manager.


Is this a true statement?  if it is, I installed the ubuntu-restricted-extra's via synaptic.  Is there a way to re-install ubuntu-restricted-extras AND have it re-install all the software that is contained (java, flash, mp3 playback, etc).

--nixIT

---

### Post by nothingspecial on 2010-05-03
I have no idea, but try opening a terminal and typing
```

sudo apt-get install ubuntu-restricted-extras
```

I promise you it will not make any problems worse.

What does it say?

---

### Post by coffeecat on 2010-05-03
> **nixIT said:**
> Is this a true statement?

I very much doubt it. :-s

---

### Post by aceracer24 on 2010-05-03
> **nixIT said:**
> Hello all,

Is this a true statement?  if it is, I installed the ubuntu-restricted-extra's via synaptic.  Is there a way to re-install ubuntu-restricted-extras AND have it re-install all the software that is contained (java, flash, mp3 playback, etc).

--nixIT

I have yet to have any problems using synaptic over command line. That said, if you are using 64 bit, the adobe flash will not install. You will need to install the beta.

---

### Post by nixIT on 2010-05-03
everything appeared to have installed, and I Have no (apparent) issues as of yet.  

It was just a question out of curiosity mostly.

Thanx for your feedback.

--nixIT

---

### Post by nothingspecial on 2010-05-03
I have 2 64 bit machines and ubuntu-restricted-extras works for me.

---

