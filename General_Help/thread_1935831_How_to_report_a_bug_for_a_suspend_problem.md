---
title: "How to report a bug for a suspend problem"
date: 2012-03-05
forum: General Help
---

### Post by splater on 2012-03-05
Hi,

I have a P7P55D main board and under 12.04. I can enter in suspend but it will not recover it ...
I wat to use the apport-bug to report this but I can not see how to do it as I have to state the package and here it says: [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage) to repport it as a kernek problem ..

Thanks for your help
Laurent

---

### Post by mikewhatever on 2012-03-05
Actually, it says:
> Recent versions of Ubuntu use pm-utils for suspend-resume, ...

...so, 'ubuntu-bug pm-utils' should do.

If you want to report is against the kernel:

 - find out which kernel version is in use
```
uname -r
```

 - find the package name
```
dpkg -i | grep linux-image
```

 - then run
```
apport-bug package-name
```

---

### Post by splater on 2012-03-05
Thanks !!! 
I will do it later at home !


Laurent

---

