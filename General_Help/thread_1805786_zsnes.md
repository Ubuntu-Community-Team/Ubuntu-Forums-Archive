---
title: "zsnes"
date: 2011-07-16
forum: General Help
---

### Post by gufide on 2011-07-16
Hi, I want to install zsnes, but when I try to install it through the software centre but it says the package is not found. I'm on a 64 bit machine. Someone know a tutorial? I didn't find one work with 11.04

Thanks

---

### Post by BrendanM on 2011-07-16
It looks like ZSNES [is available]("http://packages.ubuntu.com/natty/zsnes") in the "Universe" repository for 11.04. According to [this]("https://help.ubuntu.com/community/Repositories/Ubuntu"), they should be enabled by default.

Have you tried installing through synaptic (the package manager)?

What error do you get if you enter:

sudo apt-get install zsnes

into a terminal?

Try:

sudo apt-get update

and then try installing again?


EDIT: It looks like there may be some issues with ZSNES and x64 architecture. Some people in this thread: [http://ubuntuforums.org/showthread.php?t=1636987](http://ubuntuforums.org/showthread.php?t=1636987) are recommending snes9x as an alternative.

---

### Post by gufide on 2011-07-17
The problem with 64x is not the real problem. The problem is libao2, with is replaced by libao-common in 11.04, and there have conflict between these two library, and I don't know how to solve this

EDIT: No, the package is not there for 64x machines, and can't be installed by apt-get

---

### Post by gufide on 2011-07-18
bump

---

