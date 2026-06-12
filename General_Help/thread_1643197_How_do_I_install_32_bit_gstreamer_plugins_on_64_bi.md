---
title: "How do I install 32 bit gstreamer plugins on 64 bit Ubuntu?"
date: 2010-12-11
forum: General Help
---

### Post by uaaquarius on 2010-12-11
Hi,

I'm running Ubuntu 10.10 x64. And some Wine games (e.g. Morrowind) require 32 bit gstreamer plugins to enable sound. **How can I install 32 gstreamer plugins on my 64 bit Ubuntu?**

On Fedora this is easy, you just need to explicitly provide the architecture:
```
yum install gstreamer-plugin-good.i686
```I can't figure out how to do this in Ubuntu :(

P.S. Similar [question]("http://ubuntuforums.org/showthread.php?t=1412713") was asked almost a year ago, but it has no answer :(

---

### Post by stlsaint on 2010-12-11
This should get you started...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by uaaquarius on 2010-12-12
> **stlsaint said:**
> This should get you started...
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This help shows how to locate and install packages one by one. But
```
dpkg -i
``` fails if the architecture does not much. So, I've tried ```
dpkg -i --force-architecture
``` **Do not do this**! It replaces currently installed 64 bit package, installs no dependencies and brakes all packages depending on it! 
Luckily you just can install 64 bit package in Synaptic again and fix broken packages :)

---

