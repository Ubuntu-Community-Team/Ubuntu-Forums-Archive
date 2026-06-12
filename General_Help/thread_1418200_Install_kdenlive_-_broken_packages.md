---
title: "Install kdenlive - broken packages"
date: 2010-02-28
forum: General Help
---

### Post by sombrancelha on 2010-02-28
Hello,

I'm trying to install kdenlive and I get the following error message (in Portuguese):

```

Alguns pacotes não puderam ser instalados. Isto pode significar que
você solicitou uma situação impossível ou, se você está usando a
distribuição instável, que alguns pacotes requeridos não foram
criados ainda ou foram retirados da "Incoming".
A informação a seguir pode ajudar a resolver a situação:

Os pacotes a seguir têm dependências desencontradas:
  kdenlive: Depende: melt mas não será instalado
E: Pacotes quebrados

```

which translates into something like:

```

Some packages could not be installed. This could mean that you requested
an impossible situation or, if you're using an unstable distribution,
some of the requested packages were not created or were removed from the
"Incoming".
The following information might help solving the situation:

The packages below have unmet dependencies:
  kdenlive: Depends: melt but will not be installed
E: Broken packages

```


I installed melt and retried installing kdenlive, but then it requested for two extra packages: libmlt++2 and libmlt1. When I try installing them, I have to uninstall melt. So this would go forever.

How to proceed now?

Thanks

---

### Post by philip5 on 2010-02-28
Looks like you got some badly built packages that conflict with themselves or that melt and kdenlive are from different places?

If you are trying to install kdenlive for Karmic then you'll find the latest version (at the moment 0.7.7.1) of kdenlive on my PPA on Launchpad (see my signature for more info).

---

### Post by sombrancelha on 2010-02-28
I added your PPA and I still get the same error. I'm trying to install for Karmic.

---

### Post by philip5 on 2010-03-01
Look for kdenlive, melt, mlt and mlt++ (libs too)and uninstall all kinds of packages for them. Then install kdenlive again and it should install the right dependencies. My guess is that you have old mlt/mlt++ libs or something like that installad that have conflicts in content (same content in some packages) but conflicts in package names. Could be because a number of reasons when or if you use 3rd party repositories that have named packages differently.

In your case melt is the problem that kdenlive depends on. If the above solution doesn't help try to reinstall or upgrade melt to see what error messege you get from just that package.

---

### Post by sombrancelha on 2010-03-01
I don't really get what you mean by:

> **philip5 said:**
> Look for kdenlive, melt, mlt and mlt++ (libs too)and uninstall all kinds of packages for them.

I tried uninstalling kdenlive, melt, libmlt1 and libmlt++2 with [FONT="Courier New"]sudo apt-get remove[/FONT], but it says that they are not installed, so they won't be removed.

---

### Post by philip5 on 2010-03-01
> **sombrancelha said:**
> I don't really get what you mean by:
I tried uninstalling kdenlive, melt, libmlt1 and libmlt++2 with [FONT="Courier New"]sudo apt-get remove[/FONT], but it says that they are not installed, so they won't be removed.

Kdenlive 0.7.5-1ubuntu1 that comes with Ubuntu use libmlt++2 but my kdenlive  0.7.7.1-karmic~ppa1 use libmlt++3. You can't have libmlt++2 and libmlt++3 installed at the same time as they should conflict. Which version of libmlt++ tries to install when you install melt?

Try to install kdenlive with aptitude from a terminal:
```

sudo aptitude install kdenlive
```

And look how aptitude tries to resolve the conflict but breaks and what error messages the dialig give you.

---

### Post by sombrancelha on 2010-03-02
When I try to install melt, it doesn't try to install any libmlt++, only:
libmlt-data, libmlt2 and libquicktime1.

When I try to install kdenlive through aptitude, I get the following message (translated by me, so might not be 100% accurate):

```

The packages below will be BROKEN:
  kdenlive libmlt++2 
The NEW packages below will be installed:
  dvdauthor{a} dvgrab{a} ffmpeg{a} frei0r-plugins{a} kdenlive-data{a} 
  libavdevice52{a} libavfilter0{a} libcv1{a} libcvaux1{a} libgavl1{a} 
  libhighgui1{a} libmlt-data{a} libmlt2{a} libquicktime1{a} melt{a} 
  recordmydesktop{a} swh-plugins{a} 
0 packages updated, 19 new installed 0 to be removed and 1 not updated.
It's necessary to download 12,1 MB. After unpacking, will be 36,0MB used.
The following packages have dependencies which are not met:
  kdenlive: Depends: libmlt1 but is not installable.
  libmlt++2: Depends: libmlt1 but is not installable.
The following actions will solve the dependencies:

Install the following packages:
libmlt1 [0.4.6-0ubuntu0~ppa0 (karmic, now)]
melt [0.4.4-2build1 (karmic)]

Keep the following packages in their current versions:
libmlt2 [Not installed]

The score is 20

Accept this solution?

```

I installed anyway, and kdenlive opens. However, images and videos added to the library are all distorted.

---

### Post by philip5 on 2010-03-04
Are you sure you are using my packages of kdenlive and PPA? My version use libmlt2 and libmlt++3 and not libmlt1 and libmlt++3. Same thing with melt. It should also depend of version 0.5.0 of them.

---

