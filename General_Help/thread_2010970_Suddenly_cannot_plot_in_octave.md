---
title: "Suddenly cannot plot in octave"
date: 2012-06-26
forum: General Help
---

### Post by joewandy on 2012-06-26
Hi,

My previous Octave installation was working fine, and suddenly (I think after accepting a lot of updates from update manager), I can't plot in Octave at all.

This is what I get in Octave:

```
octave:1> x = 1:10
x =

    1    2    3    4    5    6    7    8    9   10

octave:2> y = 1:10
y =

    1    2    3    4    5    6    7    8    9   10

octave:3> plot(x, y)
error: `plot' undefined near line 3 column 1
octave:3> version
ans = 3.2.4
octave:4> help plot
error: help: `plot' not found

```

This is the list of installed packages

```
$ dpkg --get-selections | grep 'octave'
octave-plot					install
octave3.2					install
octave3.2-common				install
octave3.2-htmldoc				install
qtoctave					install

```
Could anybody help me, please ? I'm running Ubuntu 12.04 LTS. Thanks !

---

### Post by Redblade20XX on 2012-06-26
Did you try this example before and it worked?

Try installing gnuplot package. 



-Red

---

### Post by steeldriver on 2012-06-26
I can't really offer any help, but I can confirm the exact same code runs (and produces a plot) with 3.2.4 on my Xubuntu 11.10 box - I don't recall having to install anything non-standard although my package list is a little different

EDIT: apparently plot.m is part of octave3.2-common, maybe that gives you a starting point - perhaps you just need to addpath("/usr/share/octave/3.2.4/m/plot")
 
```
octave3.2-common: /usr/share/octave/3.2.4/m/plot/plot.m
``````
$ dpkg --get-selections | grep 'octave'
octave-miscellaneous        install
octave-optim                install
octave-struct                install
octave3.2                    install
octave3.2-common            install

octave:1> x = 1:10
x =

    1    2    3    4    5    6    7    8    9   10

octave:2> y = 1:10
y =

    1    2    3    4    5    6    7    8    9   10

octave:3> plot(x,y)
octave:4> version
ans = 3.2.4
```

---

### Post by joewandy on 2012-06-27
For an unknown reason, plotting works fine again after I restarted Ubuntu. Probably some leftover from the previous system update?

This is starting to resemble Windows :lolflag: Thanks for the help, everyone !

---

