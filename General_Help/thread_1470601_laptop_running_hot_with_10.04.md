---
title: "laptop running hot with 10.04"
date: 2010-05-03
forum: General Help
---

### Post by kennethtb on 2010-05-03
Hi I know this is not very exact and scientific but placing my hand under my laptop (HP Presario v6000 2gig Intel) _is noticably hotter_ and this effect is only with 10.04 32bit fresh install from ubuntu download center - no other partitions. ps my fan worked fine with windows7.. prior installation.
anyone else tried this??

---

### Post by JimTaverna on 2010-05-03
I've hit a few threads on issues regarding power saving and heat. Should be easy enough to find it, either here or on Google.

In any case, you might want to get an idea as to what's going on in your machine.

PowerTOP measures power consumption and details which processes prevent idle states. HTOP is a graphical system process monitor. Conky can give you a rudimentary temp reading, though there are better options. All can be installed from Synaptic, I believe, or via apt-get.

There may be other tools available to help you determine if your laptop is, in fact, running hotter than under Windows.

---

### Post by clhsharky on 2010-05-03
HI kennethtb

It would be helpful if we knew what video chip you have.

Run code in terminal.
```
lspci -nn | grep VGA
```

And post results, unless you already know what it is.
You might need to install a driver, or a app.

Sharky

---

