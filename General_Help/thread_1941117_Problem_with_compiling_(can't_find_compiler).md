---
title: "Problem with compiling (can't find compiler)"
date: 2012-03-15
forum: General Help
---

### Post by tjberens on 2012-03-15
I just downloaded xAutoClick and tried to install it, but every time I try running ./configure, it says it can't find the compiler. I've already installed build-essentials and all the other packages that it recommends in the install file. Anybody know what's going on?

---

### Post by lrgmmc on 2012-03-15
have you checked getdeb? they have it compiled already, unless there is somthing you needed to add while compiling. [http://www.getdeb.net/updates/Ubuntu/11.10/?q=xAutoClick]("http://www.getdeb.net/updates/Ubuntu/11.10/?q=xAutoClick")

---

### Post by tjberens on 2012-03-15
> **lrgmmc said:**
> have you checked getdeb? they have it compiled already, unless there is somthing you needed to add while compiling. [http://www.getdeb.net/updates/Ubuntu/11.10/?q=xAutoClick]("http://www.getdeb.net/updates/Ubuntu/11.10/?q=xAutoClick")

Aha, looks like that'll work. Thanks! :)

---

### Post by The Cog on 2012-03-15
If you still want to compile, note that the compiler and associated programs are all part of the **build-essential** package, which is in the repositories.

---

### Post by tjberens on 2012-03-15
> **The Cog said:**
> If you still want to compile, note that the compiler and associated programs are all part of the **build-essential** package, which is in the repositories.

Yeah, I already had that installed. I noted that in my first post.

---

### Post by mc4man on 2012-03-15
Just so you're not wasting any more time - 
That source will only recognize gcc-4.4/g++-4.4 or earlier, I'm on 12.04 (gcc-4.6), you may have gcc-4.5

Additional it will have some other errors even when provided & pointed towards 4.4
It is possible to build but you might as well use the getdeb package.

Required editing the Makefile  - line 139, replace red line with blue, (just remove the -qt4
```

	[COLOR="Red"]moc-qt4 -oguiqt4-moc.cpp guiqt4.h[/COLOR]
	[COLOR="Blue"]moc -oguiqt4-moc.cpp guiqt4.h[/COLOR]
```

The guiqt4.cpp - adding blue line at line 22
```

 #include "guiqt4.h"
 [COLOR="Blue"]#include <stdio.h>[/COLOR]
```


Installing gcc-4.4 * g++-4.4
Editing the configure like this - starting line 32
```
_debug=
_cc=gcc[COLOR="Blue"]-4.4[/COLOR]
_ccfordeps="$_cc -MM"
_cxx=g++[COLOR="Blue"]-4.4[/COLOR]

```
Then it would configure, make & run, hardly worth the effort considering a .deb is available

---

