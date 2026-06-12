---
title: "libwxgtk unresolvable dependency"
date: 2009-10-05
forum: General Help
---

### Post by beastrace91 on 2009-10-05
So I am attempting to install the latest wxMaxima from a .deb file I obtained source forge [here](http://sourceforge.net/projects/wxmaxima/) 

How ever I am unable to resolve the following unmet dependency: ```
Error: Dependency is not satisfiable: libwxgtk2.4 (>= 2.4.2.6)
```

That latest version of 2.4 I found via Ubuntu package search is 2.4.1 (which I installed and does not work for this)

Suggestions on where I can find this package or other things I can do to resolve the issue?... I am attempting to do this on my Karmic 32bit system.

Thanks,
~Jeff

PS: Installing Maxima/wxMaxima via apt-get is not as option as I need the latest version.

---

### Post by Giblet5 on 2009-10-05
It looks like you'll have to build from source.

The bleeding edge is like that and, if you eliminate the bleeding part, it's just an edge.

---

### Post by beastrace91 on 2009-10-05
Suggestions on where I can find the source? I've been poking around online and can't seem to find it anywhere :confused:

~Jeff

---

### Post by Bachstelze on 2009-10-05
Probably this:

[http://downloads.sourceforge.net/project/wxmaxima/wxMaxima/0.8.3a/wxMaxima-.8.3a.tar.gz](http://downloads.sourceforge.net/project/wxmaxima/wxMaxima/0.8.3a/wxMaxima-.8.3a.tar.gz)

---

### Post by Giblet5 on 2009-10-05
> **Bachstelze said:**
> Probably this:

[http://downloads.sourceforge.net/project/wxmaxima/wxMaxima/0.8.3a/wxMaxima-.8.3a.tar.gz](http://downloads.sourceforge.net/project/wxmaxima/wxMaxima/0.8.3a/wxMaxima-.8.3a.tar.gz)

+1 on this.

SourceForge (usually) provides source distributions on the download pages.

---

### Post by beastrace91 on 2009-10-05
Yep I actually just found that. Got it compiling now (go slow processors :/)

Anywho out of curiosity though where abouts would I go to get the libwxgtk 4.2.2.6? It is not listed on the wxWidgets source forge page.

~Jeff

---

