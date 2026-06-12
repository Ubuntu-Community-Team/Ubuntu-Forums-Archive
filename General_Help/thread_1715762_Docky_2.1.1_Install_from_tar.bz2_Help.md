---
title: "Docky 2.1.1 Install from tar.bz2 Help"
date: 2011-03-27
forum: General Help
---

### Post by TexasRussian on 2011-03-27
Hey,

I'm currently trying to install Docky version 2.1.1 fome tar.bz2 and I have tried everything I can think of and everything I could get my hands on from google, so far no luck.

I am usung Ubuntu 10.10 Maverick Meercat x64

      Things I've tried:

[LIST]
[*]./configure
[*]sudo make install
[*]make
[*]install
[/LIST]
This is what is left over after I ran ./configure:
[http://img858.imageshack.us/img858/4527/texasrussianterminal.png](http://img858.imageshack.us/img858/4527/texasrussianterminal.png)

And these are the contents of the Docky-2.1.1 file after extraction:
[http://img12.imageshack.us/img12/2944/docky211005.png](http://img12.imageshack.us/img12/2944/docky211005.png)

Any help would be greatly appreciated ^_^

---

### Post by Enigmapond on 2011-03-27
According to the PPA [https://launchpad.net/ubuntu/+source/docky](https://launchpad.net/ubuntu/+source/docky) the version you are trying to install is for Natty...the current stable version for Maverick is 2.0.7-1 You may want to just add the PPA and install it from there.

---

### Post by TexasRussian on 2011-03-27
hmmm, when I try installing the Maverick package after doing the two previous steps from here:
[http://www.ubuntuupdates.org/ppa/docky?dist=maverick](http://www.ubuntuupdates.org/ppa/docky?dist=maverick)
I get these two codes at the end of the terminal:
```
E: Unable to locate package 2.2.0~bzr1805-0ubuntu1~10.10~dockycore1
E: Couldn't find any package by regex '2.2.0~bzr1805-0ubuntu1~10.10~dockycore1'
```

---

### Post by Enigmapond on 2011-03-27
Well, I'm not sure what 2 steps you are referring to... add the ppa:

```
sudo add-apt-repository ppa:docky-core/ppa
```
then:
```
sudo apt-get update && sudo apt-get install docky
```

---

### Post by TexasRussian on 2011-03-27
Yay!, it worked,
thank you thank you thank you! :D

---

### Post by Enigmapond on 2011-03-27
Glad to help. Please mark this thread as "solved" in the thread tools.

Cheers!

---

