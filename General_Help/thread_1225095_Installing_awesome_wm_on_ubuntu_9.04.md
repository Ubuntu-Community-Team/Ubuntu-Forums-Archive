---
title: "Installing awesome wm on ubuntu 9.04"
date: 2009-07-28
forum: General Help
---

### Post by akrchstn on 2009-07-28
I'm just following [this guide]("http://awesome.naquadah.org/wiki/Awesome-3-Ubuntu-git") and the readme inside the awesome-3.2.2 folder and when I get to cmake awesome-3.2.2 it says ```
-- convert not found.
CMake Error at awesomeConfig.cmake:41 (message):
  convert is required to build awesome
Call Stack (most recent call first):
  awesomeConfig.cmake:62 (a_find_program)
  CMakeLists.txt:15 (include)
```I can't find convert anywhere and I don't even know what the second part means.
Any help

---

### Post by Aizawa on 2009-07-28
I believe awesome is in the repos :)

---

### Post by akrchstn on 2009-07-28
Oh wow, I just spent the last hour trying to do this and there it is in synaptic :(

---

### Post by EkaÏnfinitos on 2009-08-07
Awesome is in the repos, but it is an old version. I'm trying to build 3.3.2 have no idea what this "convert" of which it speaks is or how to get it.

EDIT::I'm going to attempt Awesome via git as per this guide, I'll let you know how things go.

[http://awesome.naquadah.org/wiki/Awesome-3-git-Ubuntu-Intrepid](http://awesome.naquadah.org/wiki/Awesome-3-git-Ubuntu-Intrepid)

---

### Post by Warpnow on 2009-08-19
If you are brave, Karmic beta has a much more updated version of Awesome.

---

### Post by asp_id on 2009-09-11
"convert" is a part of ImageMagic, therefore it wants ImageMagic =)

---

