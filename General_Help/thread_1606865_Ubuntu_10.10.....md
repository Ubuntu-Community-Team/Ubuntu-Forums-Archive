---
title: "Ubuntu 10.10?...."
date: 2010-10-27
forum: General Help
---

### Post by VcDeveloper on 2010-10-27
I was about to down the 10.10 version and notice it recommended the x32.  Whats wrong with the x64, because I'm currently running 10.04 LTS on my main server and want to upgarde to 10.10.

...also why isn't my update manager giving me the upgrade option?

---

### Post by IIC0RRUPT10NII on 2010-10-27
There should not be anything wrong with 64 bit, they recommend 32 bit always over 64 I believe.. someone correct me if I am mistaken

---

### Post by darolu on 2010-10-27
I don't see anything *wrong* with the x86-64 (amd64) version; they recommend the x86 (32-bit) one because you may not find every program available for the 64-bit version of Ubuntu, running this 32bit-only applications is possible in 64-bit systems but some tweaking is needed (basically install and configure 32-bit libraries). If you haven't found any problem with the 64-bit version of Ubuntu, go ahead and keep using it, programs that are properly written for 64-bit systems really fly on them.

To upgrade press Alt+F2 and run:
```
update-manager -d
```

---

### Post by Verbeck on 2010-10-27
GUI method for upgrading:
in synaptic, go to settings, repositories, updates tab. on the bottom there will be **release upgrade**. from the drop down list select Normal releases

---

### Post by VcDeveloper on 2010-10-27
Thanks everyone for your help! :)

---

