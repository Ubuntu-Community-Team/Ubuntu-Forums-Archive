---
title: "Different GCC versions on Ubuntu 10.04"
date: 2010-09-07
forum: General Help
---

### Post by tdnghia89 on 2010-09-07
Hi, I am using Ubuntu 10.04. The default GCC install is GCC 4.4.3. However, one of my program need GCC 4.1.1 to run. I install it exactly as shown in this link : [http://www.cs.brown.edu/research/borealis/public/install/install.select.html#ccache](http://www.cs.brown.edu/research/borealis/public/install/install.select.html#ccache)[B][B]> gunzip gcc-4.1.1.tar.gz
> tar  xvf  gcc-4.1.1.tar
> mkdir  gcc_obj
> cd     gcc_obj/
> ../gcc4.1.1/configure --program-suffix=-4.1.1  --prefix=${BOREALIS_SOFTWARE}/gcc
> make bootstrap
> make install
[/B][/B] After installing, I type gcc --version. The result is still : gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3. Do I miss anything ?
Can anyone help me to make gcc-4.1.1 become the default version ? I really appreciate your help.

---

### Post by dcstar on 2010-09-07
> **tdnghia89 said:**
> Hi, I am using Ubuntu 10.04. The default GCC install is GCC 4.4.3. However, one of my program need GCC 4.1.1 to run. I install it exactly as shown in this link : [http://www.cs.brown.edu/research/borealis/public/install/install.select.html#ccache](http://www.cs.brown.edu/research/borealis/public/install/install.select.html#ccache)[B][B]> gunzip gcc-4.1.1.tar.gz
> tar  xvf  gcc-4.1.1.tar
> mkdir  gcc_obj
> cd     gcc_obj/
> ../gcc4.1.1/configure --program-suffix=-4.1.1  --prefix=${BOREALIS_SOFTWARE}/gcc
> make bootstrap
> make install
[/B][/B] After installing, I type gcc --version. The result is still : gcc (Ubuntu 4.4.3-4ubuntu5) 4.4.3. Do I miss anything ?
Can anyone help me to make gcc-4.1.1 become the default version ? I really appreciate your help.
```
whereis gcc
man update-alternatives
```

---

### Post by tdnghia89 on 2010-09-09
Thank you !

---

