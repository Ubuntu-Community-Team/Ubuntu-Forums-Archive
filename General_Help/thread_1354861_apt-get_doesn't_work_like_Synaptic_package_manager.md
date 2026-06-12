---
title: "apt-get doesn't work like Synaptic package manager"
date: 2009-12-14
forum: General Help
---

### Post by rgoytacaz on 2009-12-14
Hello there,

While trying to install Ruby on Rails + Apache on my Dell Ubuntu Laptop, I started having some troubles following a couple of tutorials.

Well, I found out that, When installing through Synaptic stuff seems to work as expected, but while doing apt-get install *package* (Which all tutorials tell you to do, USE THE TERMINAL!!! fever) it just doesn't update something that leads my system to think its not installed.

Example..

sudo apt-get install rubygems1.9

after the installations..

gem -v
program not found.

if I did install it through Synaptic..

gem -v 
Ruby Gems 1.3.5

And this is happening for everything.

I read somewhere that you need to update some symlinks, do I really need to?
and how do I know which ones should I create?

This is messed up.

Im using Karmic Koala 9.10

Also my wireless (Broadcom - b43,ssb) doesn't work =/ (used to work on 9.04
 (I've already upgraded all the packages, still nothing)

Thx

---

### Post by ankspo71 on 2009-12-14
Hi,
I'm still relatively new to the command line, but I have been enjoying learning it so far. I have noticed when I am not able to launch a program with a single command, I have to resort to providing the path to the executable.

I don't have Ruby on Rails or Apache on my system so I will use firefox as an example.

If **firefox-3.5 -v** doesn't work, I know that **/usr/bin/firefox-3.5 -v** will. In the case of my installed version of firefox, it works both ways, but I have seen several programs in the past that did not have a single command to launch them.I haven't noticed a difference between installing from apt-get or synaptic, but in all fairness, I have not ever compared the installations either.

If you are looking for info on how to create a symlink, see the following informations in the terminal. (I haven't experimented with creating links yet, so I can't provide an example)

```
man ln
ln --help
info ln
```

 I just found this page from Ubuntu that talks about symlinks. 
[http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html](http://manpages.ubuntu.com/manpages/jaunty/man7/symlink.7.html)

---

### Post by rgoytacaz on 2009-12-14
Any1 else on this?

---

### Post by jobix on 2009-12-14
Check your PATH variable:

> echo $PATH

Check where that executable is:
> which gemv

Does your PATH variable include the path to the executable?

---

