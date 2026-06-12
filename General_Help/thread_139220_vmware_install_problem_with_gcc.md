---
title: "vmware install problem with gcc"
date: 2006-03-03
forum: General Help
---

### Post by steharg on 2006-03-03
hello all, fantastic forum.. newbie here needing a little help.

need a little help installing vmware workstation.
I installed it ok last week as a test on the same system on breezy and it installed ok allbeit after installing the kernel headers.

now ive come to install it again after i have done a new install on my computer and im running into problems which are out of my depth

> Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.plwith CC environment variable pointing to the "gcc" version "3.4.5".

can anyone help please?

---

### Post by MartinG on 2006-03-03
You need to install gcc-3.4 (sudo apt-get install gcc-3.4), and then you need to use it, thus:```

export CC=gcc-3.4
<vmware installation command>
```

---

### Post by steharg on 2006-03-04
thanks for that
so easy when you know how! :)

---

