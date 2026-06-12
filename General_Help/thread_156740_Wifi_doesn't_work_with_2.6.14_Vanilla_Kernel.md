---
title: "Wifi doesn't work with 2.6.14 Vanilla Kernel"
date: 2006-04-07
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-04-07
It doesn't work. Should I just go back to my old kernel ? Or upgrade to a new one ? I added ndiswrapper to ndiswrapper to etc/modules but nothing seems to work. Also, no connections appear under System > Administration > Networking. Can I create a new connection ? ](*,)

---

### Post by trent dillman on 2006-04-07
Either try inserting it:

```
sudo modprobe ndiswrapper
```

or if that doesn't work, compile your own version...

---

### Post by xXx 0wn3d xXx on 2006-04-07
[QUOTE=trent dillman]Either try inserting it:

```
sudo modprobe ndiswrapper
```

or if that doesn't work, compile your own version...[/QUOTE]
I tried that many times but I get FATAL: Module "ndiswrapper" not found. Maybe I'll go and compile the 2.6.16.2 kernel-or I'll just use my old one.

---

### Post by trent dillman on 2006-04-07
Download the ndiswrapper source package, and compile a version for your kernel.

---

### Post by xXx 0wn3d xXx on 2006-04-07
[QUOTE=trent dillman]Download the ndiswrapper source package, and compile a version for your kernel.[/QUOTE]
Yeah, that's basically what I'm doing :). I'm not exactly recompiling the kernel, I'm making a custom kernel header.

---

### Post by trent dillman on 2006-04-07
here, step by step:

```

sudo -s
apt-get -y install ndiswrapper-source
cd /opt
tar jxvf /usr/src/ndiswrapper-source.tar.bz2
cd ndiswrapper*
make install

```

---

### Post by xXx 0wn3d xXx on 2006-04-07
[QUOTE=trent dillman]here, step by step:

```

sudo -s
apt-get -y install ndiswrapper-source
cd /opt
tar jxvf /usr/src/ndiswrapper-source.tar.bz2
cd ndiswrapper*
make install

```[/QUOTE]
Nope it didn't work. The kernel won't use wifi. Wtf ? Why am I even trying to fix this kernel when my 2.6.12-10-k7 kernel works great ? Maybe I'll try to compile the latest kernel from kernel.org or just use my current kernel.

---

