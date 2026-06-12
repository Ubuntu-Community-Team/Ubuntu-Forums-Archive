---
title: "Upgrade to previously purged kernel with apt-get upgrade"
date: 2010-09-27
forum: General Help
---

### Post by peap on 2010-09-27
I was running kernel 2.6.32-24 but due to some driver issues downgraded to kernel 2.6.32-23 and purged the 2.6.32-24 kernel (apt-get purge).

I now wish to upgrade to kernel 24 again using apt-get upgrade as the driver mentioned above is now added to my dkms tree and should be properly recompiled (as far as I understand). I tried:

```
sudo apt-get install linux-image-2.6.32-24-generic linux-headers-2.6.32-24-generic

```

.. but the dkms recompile did not run (kernel 24 was installed). When trying to apt-get upgrade the 24 kernel isn't found (as I purged it I assume).

---

### Post by philinux on 2010-09-27
Run this and post back.

```
dpkg -l | grep ^ii | grep 2.6.32 | awk -F' ' '{ print $2 }'
```

---

### Post by peap on 2010-09-27
```
linux-headers-2.6.32-22
linux-headers-2.6.32-23
linux-headers-2.6.32-23-generic
linux-headers-2.6.32-24
linux-image-2.6.32-23-generic
linux-libc-dev
lirc-nct677x

```

Seems kernel 24 isn't totally wiped? Would...
```
sudo dpkg --purge linux-headers-2.6.32-24
```
... allow me to do a apt-get upgrade to kernel 24?

---

### Post by philinux on 2010-09-27
> **peap said:**
> ```
linux-headers-2.6.32-22
linux-headers-2.6.32-23
linux-headers-2.6.32-23-generic
linux-headers-2.6.32-24
linux-image-2.6.32-23-generic
linux-libc-dev
lirc-nct677x

```

Seems kernel 24 isn't totally wiped? Would...
```
sudo dpkg --purge linux-headers-2.6.32-24
```
... allow me to do a apt-get upgrade to kernel 24?

No just this is missing.
```
sudo apt-get install linux-image-2.6.32-24-generic linux-headers-2.6.32-24-generic
```

---

### Post by peap on 2010-09-27
Will doing that recompile the dkms modules properly? I thought I needed to use apt-get upgrade?

How do I make the apt-get upgrade "find" kernel 24 again?

---

