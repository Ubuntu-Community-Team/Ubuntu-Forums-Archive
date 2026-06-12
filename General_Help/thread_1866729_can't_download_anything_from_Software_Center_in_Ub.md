---
title: "can't download anything from Software Center in Ubuntu 11.10"
date: 2011-10-21
forum: General Help
---

### Post by rezbd on 2011-10-21
Just have installed Ubuntu 11.10 on my netbook. It's running fine. And I can browse internet in firefox. But I can't download anything from software center. Even I failed to download Synaptic Manager from Software Center!!

What can I do now?

---

### Post by e79 on 2011-10-21
Can you try from the terminal ?

```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install synaptic
```

---

### Post by rezbd on 2011-10-21
thanks. I've just tried it from terminal. it shows:

> Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by e79 on 2011-10-21
huh...weird....what does this returns ?

```
apt-cache search synaptic
```

---

### Post by rezbd on 2011-10-22
after putting 
apt-cache search synaptic
it shows:

> xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server
sessioninstaller - APT based installer using PackageKit's session DBus API

---

### Post by mynameissagarbhatt on 2011-10-22
i faced the same problem.....write this in terminal:
```
gksudo software-center
```

---

### Post by rezbd on 2011-10-22
@mynameissagarbhatt it didn't work either :( whatever I try to get from the software center, it always shows "**failed to download repository information**"

---

### Post by mikejonesey on 2011-10-22
this is more than likley caused by your repo mirrors being down, just open system>admiin>software sources and select a different mirror...

if it's not the mirror, then it's network / proxy stuff...

newhos let me know how is after twidling the software sources and running an apt-get update (should auto triger after changing sources...)

---

### Post by rezbd on 2011-10-22
after changing the mirror Bangladesh server to US server, now I can download softwares from the Software Center.

Thousand thanks :)

---

### Post by e79 on 2011-10-22
I'm glad your issue is resolved !

Cheers

---

### Post by rezbd on 2011-10-23
@e79 thanks :popcorn:

---

