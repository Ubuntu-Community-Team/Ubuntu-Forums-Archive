---
title: "Binutils sitecom MD253"
date: 2010-09-27
forum: General Help
---

### Post by zainka on 2010-09-27
Hi

I try to install the binutils from the source of my sitecom MD253 NAS disk. However, running the config script reveale some problems like below:


> checking for gm4... no
checking for gnum4... no
checking for dlltool... no
checking for lipo... no
checking for windres... no
checking for windmc... no


Regarding gm4 and gnum4 (M4) i think the config file is messing arround because M4 is recently installed. By some means config wont find the macro processor. May be a path issue. (bison is ver 2.4.1 autoconf is ver 2.65)

For the 4 last items i have problems identifying which packages they belong to. Any clue? Lipo seems to be related to darwin somehow, but I dont need to build darwin... The three others, are they some cind of a script I could install in my /usr/bin ?? I found some scripts but would like to have it confirmed to be script and not binaries I should look for. Any ifficial sites where they could be downloaded from?

Thanks in advance

---

