---
title: "3rd query about removing development libraries"
date: 2009-07-29
forum: General Help
---

### Post by tanixmukherzee on 2009-07-29
recently i downloaded and installed audacious-2.1 according to the instructions given in this blog - [http://tuxarena.blogspot.com/2009/07/how-to-compile-and-install-audacious-21.html.Now](http://tuxarena.blogspot.com/2009/07/how-to-compile-and-install-audacious-21.html.Now) my question is if i uninstall the audacious package and the plugins also the developent libraries initially installed were not removed. How to remove them? Any idea?
(I am sure the development libraries are not removed because when after uninstalling i again retyped - [COLOR=#006600]sudo apt-get build-dep audacious , it showed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded...that means the development libraries for audacious 2.1 are still there and i want to get rid off them):(
[/COLOR]

---

### Post by c0mput3r_n3rD on 2009-07-29
> **tanixmukherzee said:**
> recently i downloaded and installed audacious-2.1 according to the instructions given in this blog - [http://tuxarena.blogspot.com/2009/07/how-to-compile-and-install-audacious-21.html.Now](http://tuxarena.blogspot.com/2009/07/how-to-compile-and-install-audacious-21.html.Now) my question is if i uninstall the audacious package and the plugins also the developent libraries initially installed were not removed. How to remove them? Any idea?
(I am sure the development libraries are not removed because when after uninstalling i again retyped - [COLOR=#006600]sudo apt-get build-dep audacious , it showed 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded...that means the development libraries for audacious 2.1 are still there and i want to get rid off them):(
[/COLOR]

Did you try:
```

sudo apt-get remove audacious

```
?

---

### Post by tanixmukherzee on 2009-07-30
yeah...i hv done that...i have removed audacious.but when i am entering sudo apt-get build-dep audacious again it shows 0 upgraded 0 newly installed....that means development libraries are still there...how to remove them...anybody else want to help...

---

### Post by aesis05401 on 2009-07-30
> **tanixmukherzee said:**
> yeah...i hv done that...i have removed audacious.but when i am entering sudo apt-get build-dep audacious again it shows 0 upgraded 0 newly installed....that means development libraries are still there...how to remove them...

```

sudo apt-get purge <package-name> 

```

Does this work for you??  Remove leaves behind config files and stuff in addition to the original packages themselves.. There are other options like autoclean.  They are listed in man apt-get.

---

### Post by tanixmukherzee on 2009-07-30
i hv tried it.the result shows--

 sudo apt-get purge audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package audacious is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

my point is if audacious and all the dev libs were completely removed then in a reinstall attempt sudo apt-get build-dep audacious would have shown the complete list of dev libs to be installed,isn't it?
Insted it's showing 
---0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.doesnt that mean the dev. libs are still there? So how to delete them...cause i remember it was a huge list of development libraries.
And yes i have tried autoremove,autoclean,clean all of them.None helped. Anymore suggestions?:confused:

---

### Post by tanixmukherzee on 2009-07-30
i expected more suggestions in this thread...

---

### Post by aesis05401 on 2009-07-30
Alright, try apt-get autoremove.

Does this work for you?

---

