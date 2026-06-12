---
title: "Cannot update or fix broken package"
date: 2011-02-01
forum: General Help
---

### Post by thestitch on 2011-02-01
On my 10.04 desktop I can't install or update any packages. I get an error regarding unmet dependencies. When I run apt-get -f install or use synaptic to fix broken packages it hangs at:

Preparing to replace libc-bin 2.11.1-ubuntu7.2 (using .../libc-bin_2.11.1-0ubuntu7.8_i386.deb) ...
Unpacking replacement libc_bin...

It never gets past there, and I have to reboot and run dpkg --configure -a to allow synaptic to launch again.

---

### Post by bazman79 on 2011-02-02
I have a similar problem with 10.04 Server, hangs on the same package. I also tried downgrading, with no luck (same package hangs).

---

### Post by thestitch on 2011-02-02
Does this mean the new libc-bin package is corrupt? 

I'm trying to update the packages by downloading the debs for libc-bin, libc6-dev, and libc-6. When I try to install libc6-dev it hangs at the same place. How do I force it to use the downloaded libc-bin?

---

### Post by plucky on 2011-02-02
> **thestitch said:**
> Does this mean the new libc-bin package is corrupt? 

I'm trying to update the packages by downloading the debs for libc-bin, libc6-dev, and libc-6. When I try to install libc6-dev it hangs at the same place. How do I force it to use the downloaded libc-bin?

```
sudo apt-get clean
```

will clear out all the .deb files from /var/cache/apt/archives and it will have to download a new set of files.You could at the same time try another server.

Good Luck

---

### Post by thestitch on 2011-02-02
I tried sudo apt-get clean, and new debs were downloaded, but I;m still getting hung at Unpacking replacement libc-bin ...

---

