---
title: "Trying to Install from Tarball"
date: 2012-01-30
forum: General Help
---

### Post by superawesomepanda on 2012-01-30
I got fairly far and then I got this error:

panda@Amaranth:/usr/local/src/MissionLab-7.0/src$ make all
make -q -C ipt/src/communications/ipt || make iptserver
make[1]: Entering directory `/usr/local/src/MissionLab-7.0/src'
\n...building the IPT libraries...\n
cd ipt/src/communications/ipt; ./configure -unix LINUX -vx "" -install LINUX -main LINUX
./configure: 172: imake: not found
make[1]: *** [iptserver] Error 127
make[1]: Leaving directory `/usr/local/src/MissionLab-7.0/src'
make: *** [all] Error 2


I tried searching for "imake not found" on Google but couldn't find anything to fix this. Any suggestion?

---

### Post by drmrgd on 2012-01-30
Looks like imake is part of the package xutils-dev.  Try getting that package and recompiling your program.

---

### Post by Rodney9 on 2012-01-30
Ubuntu Installation Notes - 

[http://code.google.com/p/soar/wiki/MissionLab](http://code.google.com/p/soar/wiki/MissionLab)

Rodney

---

### Post by drmrgd on 2012-01-30
> **Rodney9 said:**
> Ubuntu Installation Notes - 

[http://code.google.com/p/soar/wiki/MissionLab](http://code.google.com/p/soar/wiki/MissionLab)

Rodney

Good catch!  Please disregard my advice and follow Rodney's.  There is much more involved than just adding the package I recommended.

---

### Post by superawesomepanda on 2012-01-30
> **Rodney9 said:**
> Ubuntu Installation Notes - 

[http://code.google.com/p/soar/wiki/MissionLab](http://code.google.com/p/soar/wiki/MissionLab)

Rodney

Oh wow that's awesome. Thanks.

---

