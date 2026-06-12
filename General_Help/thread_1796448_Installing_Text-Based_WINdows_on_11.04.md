---
title: "Installing Text-Based WINdows on 11.04"
date: 2011-07-03
forum: General Help
---

### Post by Pard68 on 2011-07-03
Been searching around for a few days. So far I have found three previous topics on this and all of them are useless/out of date.

I'm trying to install [http://linuz.sns.it/~max/twin/](http://linuz.sns.it/~max/twin/) on my Ubuntu 11.04 machine. 

I've tried making it from the binary on the site and I get a bunch of errors when I try to "make" it. I've attached the output from make.

Anyone know how to get this to work? I found a tutorial that said you had to find the .module files and remove all the "-e"s but I cannot find any .module files.

---

### Post by Pard68 on 2011-07-05
B-u-m-p

---

### Post by marshag63 on 2011-07-07
Looking at the make text, you seem to be missing a dependency related to libTutf.

I tried building twin from the stable version (not sure which one you chose) and get an error related to libTT.


MDG

---

