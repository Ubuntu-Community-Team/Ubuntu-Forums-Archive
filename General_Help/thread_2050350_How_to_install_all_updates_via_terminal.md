---
title: "How to install all updates via terminal?"
date: 2012-08-30
forum: General Help
---

### Post by kerryhall on 2012-08-30
I have noticed that I still get the update manager popping up after doing a:

sudo apt-get update
sudo apt-get upgrade 

and installing all updates. It appears that updates can be in one or both categories: 
GUI update manager
terminal update manager

Since I am seeing the GUT update manager ask to install packages that are not mentioned by the terminal update manager. 

How do I install all updates via the terminal only?

---

### Post by lukeiamyourfather on 2012-08-30
They are both the same as far as I know. What kind of updates is the GUI showing? Are they distribution upgrades or individual packages?

---

### Post by black veils on 2012-08-30
you need to do ```
sudo apt-get dist-upgrade
```
this does not do a version upgrade, it is the equivalent of what the GUI method uses.

---

### Post by lukeiamyourfather on 2012-08-30
> **black veils said:**
> you need to do ```
sudo apt-get dist-upgrade
```
this does not do a version upgrade, it is the equivalent of what the GUI method uses.

What's the difference? Just newer kernels?

---

### Post by black veils on 2012-08-30
upgrade only updates software already on the system, it does not remove or add anything else.

dist-upgrade allows also the removal of obsolete packages, when it required by installing something new, for example. i am not good at explaining, but upgrade alone is a stunted way to do things, so you will get errors sometimes, as it is restricted.

EDIT:
[http://ubuntulinuxtipstricks.blogspot.co.uk/2010/02/dist-upgrade-misnomer-confusion.html](http://ubuntulinuxtipstricks.blogspot.co.uk/2010/02/dist-upgrade-misnomer-confusion.html)

---

### Post by kerryhall on 2012-08-30
In the GUI updater, I'm seeing various kernel packages and other things. I should have done a screenshot of it. :P Maybe I will in a few weeks or so.

So it sounds like:
sudo apt-get dist-upgrade

Is the command I should be using. 

Thanks for the help everyone!

---

