---
title: "apt-get can't find package"
date: 2010-08-25
forum: General Help
---

### Post by franticpedantic on 2010-08-25
Hi, 

I am trying to cross compile ffmpeg with mingw by following this guide. 

[http://ffmpeg.arrozcru.org/wiki/index.php?title=Main_Page](http://ffmpeg.arrozcru.org/wiki/index.php?title=Main_Page)

It uses some packages that are hosted here: 

[http://apt.arrozcru.org/](http://apt.arrozcru.org/)

You can see there is a package mingw32-w32api on there. So I add to my /etc/apt/sources.list 

deb [http://apt.arrozcru.org](http://apt.arrozcru.org) ./
deb-src [http://apt.arrozcru.org](http://apt.arrozcru.org) ./

and it seems to update fine from there when I apt-get update. However when I try to apt-cache search mingw32-w32api nothing turns up, and when I try to apt-get install it it says it can't find the package.

I'm guessing I'm misunderstanding something about apt-get? Any pointers would be greatly appreciated, thanks.

---

### Post by wojox on 2010-08-25
It's not a package, but a [Directory]("http://apt.arrozcru.org/mingw32-w32api/")

---

### Post by franticpedantic on 2010-08-25
Yeah that was silly of me.

I have actually come back to this problem, and I remembered that I did see something on their forums about their not being a 32 bit version or something, but that I shouldn't need that package anyway. I think that packages are not the problem. Compiling ffmpeg seems to be quite a moving target for some reason :-\.

---

