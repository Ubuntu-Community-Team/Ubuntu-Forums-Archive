---
title: "Why does this package exist only on Hoary and not on Breezy"
date: 2006-03-08
forum: General Help
---

### Post by harisund on 2006-03-08
[http://packages.ubuntu.com/hoary/electronics/ngspice](http://packages.ubuntu.com/hoary/electronics/ngspice)

I am not able to find the ngspice on Breezy. Any reason? Do I need to add hoary's Universal repository? 

Thanks !

---

### Post by Xian on 2006-03-08
It is in the Universe group, and AFAIK the pkg was dropped from Debian's official repos, so that would explain why it no longer shows up in later versions of Ubuntu. In short, it is no longer there to be syncd and placed in Ubuntu's more current builds.

---

### Post by harisund on 2006-03-08
Oh.. that doesn't sound too good.. 

So does it mean I can just add Hoary's repository and install it? 

Also, when I add Hoary's repositories to my list, will it affect other programs that I want to install? For example, if there is a package that is newer in the breezy repositories, I want that to be installed instead of Hoary's. Is it possible ? 

Thanks for your quick help ..

---

### Post by Xian on 2006-03-08
You already posted a link to the package. 
Why not just download that single deb and install locally??

No need to alter your source list over just one item....

The deps are listed there too if you need a few.

---

### Post by bagel on 2006-03-09
Hello there;

I'm also trying to get ngspice to run under Ubuntu. I tried to compile the package from source, but receive errors when including xgraph support.

Also, I seem not to be able to install the debs over the manually compiled version(which has no ability to output graphics).

Any help would be greatly appreciated,

Ciao, bagel

---

### Post by bagel on 2006-03-10
Interestingly, removing the before installed files, and afterwards forcing the *debs from the ngspice homepage to install, seems to have worked. (after a restart, strangely).

Ciao, bagel

---

