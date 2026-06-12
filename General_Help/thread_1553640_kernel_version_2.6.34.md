---
title: "kernel version 2.6.34"
date: 2010-08-15
forum: General Help
---

### Post by bprins on 2010-08-15
Hi,

Probably a simple question, but i was wondering why is there a new kernel available (2.6.34) which is not proposed in apt-get update?

Now I've got to download .deb files and upgrade manually. I would like to be able to install unstable / testing releases for packages. I have checked everything in software sources, but I still don't get the newest kernel proposed.

Another question: what are "backports"?

Hope to learn more soon.

Thanks in advance.

bas

---

### Post by CharlesA on 2010-08-15
Add the kernel PPA to get the newest kernels.

Check here: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds)

---

### Post by bprins on 2010-08-15
life can be so easy :)

thanks.

any chance you also know what "backports" are?

---

### Post by CharlesA on 2010-08-15
They are software from older versions. Check here: [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by bprins on 2010-08-15
oki,

thanks a lot.

---

### Post by xangua on 2010-08-15
how can we add that PPA¿

---

### Post by xangua on 2010-08-15
I know and use this PPA, it also improves intel & ati videocard performance

I hope it works for you

[https://launchpad.net/~guido-iodice/+archive/best-intel](https://launchpad.net/~guido-iodice/+archive/best-intel)

---

### Post by bprins on 2010-08-15
```

sudo add-apt-repository ppa:kernel-ppa/ppa
sudo apt-get update
sudo apt-get install linux-headers-2.6.35.15
sudo update-grub

```

Here comes a reboot. If I run into serious ****, I'll going to beg for more help :)

---

### Post by mike555 on 2010-08-15
can't find package

---

