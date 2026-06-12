---
title: "install java - both 32-bit and 64-bit side-by-side"
date: 2011-10-06
forum: General Help
---

### Post by hamhock on 2011-10-06
I presently have 64-bit Java JDK running on Lucid 64-bit.  I would also like to install 32-bit JRE.  Can I just go ahead and simply install the 32-bit version?  Are there any other steps necessary after the install?

---

### Post by hamhock on 2011-10-09
I installed this:
```
sudo apt-get install ia32-sun-java6-bin

```

run this to select which java version
```
sudo update-alternatives --config java
```

for those apps I want to run in 32-bit mode, I just have to add the "-client" flag to the java command.  I hope this is right and I won't run into any issues later.

---

