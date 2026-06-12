---
title: "32 bit version of libgd"
date: 2010-04-11
forum: General Help
---

### Post by jacky872 on 2010-04-11
Dear forum,

I have installed packages libgd2-xpm and libgd2-xpm-dev, and I get the following error:

/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../libgd.so when searching for -lgd
/usr/bin/ld: skipping incompatible /usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../libgd.a when searching for -lgd
/usr/bin/ld: skipping incompatible /usr/lib/libgd.so when searching for -lgd
/usr/bin/ld: skipping incompatible /usr/lib/libgd.a when searching for -lgd

What is the correct package which I should install?

Thanks!

---

### Post by jacky872 on 2010-04-11
Any help?

I forgot to mention I get the above errors while trying to compile some C++ code.

Thanks

---

### Post by Bachstelze on 2010-04-11
If you really want to compile 32-bit code on a 64-bit machine, you will need the packges gcc-multilib and ia32-libs.

---

### Post by jacky872 on 2010-04-11
Thanks but I have already installed these packages and it still gives me this -lgd error.

---

