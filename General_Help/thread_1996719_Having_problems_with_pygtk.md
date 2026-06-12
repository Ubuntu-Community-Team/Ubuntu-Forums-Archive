---
title: "Having problems with pygtk"
date: 2012-06-04
forum: General Help
---

### Post by bkama1 on 2012-06-04
Hello! I'm having problems with the pygtk package. I believe that it is properly installed but when other programs try to access it, it can't be found. On the Synaptic Package Manager it says that **python-gtk2-dev version 2.24.0-3** is installed but when I trying importing it in python it says the package cannot be found( I found out that this is one way to verify if the package is installed correctly). I've tried re-installing it a couple times but It hasn't seemed to fix the problem. 

I'm a newbie to Ubuntu so any and all help would be appreciated.

---

### Post by shafi.dude99 on 2012-06-04
> **bkama1 said:**
> Hello! I'm having problems with the pygtk package. I believe that it is properly installed but when other programs try to access it, it can't be found. On the Synaptic Package Manager it says that **python-gtk2-dev version 2.24.0-3** is installed but when I trying importing it in python it says the package cannot be found( I found out that this is one way to verify if the package is installed correctly). I've tried re-installing it a couple times but It hasn't seemed to fix the problem. 

I'm a newbie to Ubuntu so any and all help would be appreciated.
It seems that you have missing dependencies. Do, 'sudo apt-get build-dep  python-gtk2' which will download and install all required dependencies.

---

### Post by bkama1 on 2012-06-04
> **shafi.dude99 said:**
> It seems that you have missing dependencies. Do, 'sudo apt-get build-dep  python-gtk2' which will download and install all required dependencies.

Thanks shafi. This command definitely updated a few things but still no luck with pygtk when I try to import it in python. :(. Any other ideas??

---

### Post by bkama1 on 2012-06-04
Bump for great justice. Anyone have any suggestions?

---

### Post by bkama1 on 2012-06-05
Still looking for some assistance here. Not sure what I should do. 

Just tried this basically: [http://faq.pygtk.org/index.py?req=show&file=faq01.010.htp](http://faq.pygtk.org/index.py?req=show&file=faq01.010.htp)

but didn't really change anything apparently.

---

