---
title: "Is building Konqueror from source worth it?"
date: 2006-05-07
forum: General Help
---

### Post by hermesrules on 2006-05-07
I upgraded to Dapper after Flight 5, and have been quite happy with Kubuntu. Applications perform really well, and for the most part, everything is quite fast, probably faster than Breezy, although I have not done any benchmarking to be certain.

However, I was wondering if installing Konqueror with the build option in apt-get would do any good. My machine is Athlon XP 2200+, and I would like to see some better perfomance, and there is possibly performance loss due to the lack of any optimizations.

So my questions are:

- what is the exact command line syntax for dowloading Konqueror's source and compiling it through apt-get?
- how do I set it up so that it compiles optimized for my system? (Like Swiftfox, which outperforms traditional Firefox)
- will that affect my ability to upgrade Konqueror, once new versions are available in the repositories?
- is it worth the trouble? (in case someone has done it, and can testify to the performance gain)

Thanks!

---

### Post by ltmon on 2006-05-08
Konqueror itself exists in the kdebase package, HOWEVER... this will do nothing for page rendering speed (which I assume is what you want to speed up?).  What you need to do is to recompile KHTML.  It exists (I think) in the kdelibs package, so you should compile this one yourself for best results.

The actual drawing of the Konqueror window is mainly handled by the QT library, so you would probably have to build that again for any noticeable improvement in this area.

I'm not sure how much joy you will get in the end in terms of speed ups but hopefully this helps.

Maybe it's worth trying out Gentoo in a seperate partition, and you can test how much difference compiling things yourself makes and whether it's worth the effort.

Cheers,

L.

---

### Post by hermesrules on 2006-05-08
Thanks for your response. I tried Gentoo once, and the reason I abandonded it (and went with (K)Ubuntu) were the compile times... I can certainly handle several packages that need to be compiled, but when it comes to the entire system, I had neither the resources, nor the patience. However, I do remember that Gnome (I didn't do KDE back then) was remarkably faster on Gentoo than on Novel Linux Desktop, which I used prior to it.

From your description, it seems that it will hardly be worth compiling kdebase and kdelibs to get supposedly optimized Konqueror and KHTML. In fact, rendering speed in Konqueror is not slow at all, and I was thinking more in terms of overall performance both as a browser and as a file manager. I guess I will keep it as is...

---

### Post by GoldBuggie on 2006-05-08
recompiling kdelibs doesn't do much...besides..you will have to recompile it every time a new kde is out...only library that I have recompiled is libqt3-mt...sometimes i think there is a difference sometimes I do not. But  if  you want to recompile something that is the base of kde and a library doesn't get changed often(never from breezy to dapper) I recommend playing with different options on that on. I tried 5 different cimpiler options before finally staying with a good choice for me.

i got a faster computer that runs gentoo and I can't see any difference(besides that the later computer is faster).

---

