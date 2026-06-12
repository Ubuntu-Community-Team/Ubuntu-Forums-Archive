---
title: "Why do I need a C compiler to read man pages?"
date: 2011-03-08
forum: General Help
---

### Post by Mozai on 2011-03-08
Documentation for commands is typically invoked with ```
/usr/bin/man (commandname)
```
The only source of /usr/bin/man I was able to find is package 'man-db', which requires packages bsdmainutils.
bsdmainutils requires 'cpp'.

Why do I need to install a C compiler just to read the instructions that comes with each program?  
It seems excessive for what amounts to a wrapper around ```
zcat /usr/share/man/man1/lynx.1.gz |groff -man -Tascii |less
```.

---

### Post by bodhi.zazen on 2011-03-08
LOL

No, simply use man

```
man <command>
```

man pages are also available on line

[http://manpages.ubuntu.com/](http://manpages.ubuntu.com/)

---

### Post by sisco311 on 2011-03-08
> **Mozai said:**
> 
Why do I need to install a C compiler just to read the instructions that comes with each program?  


You don't. cpp is not a dependency of bsdmainutils:
```

apt-cache depends bsdmainutils 
bsdmainutils
  Depends: libc6
  Depends: libncurses5
  Depends: bsdutils
  Depends: debianutils
  **Suggests**: cpp
 |Suggests: wamerican
  Suggests: <wordlist>
...
```

EDIT:
Oh, and cpp is not a compiler. It's the [**C** **p**re**p**rocessor]("http://en.wikipedia.org/wiki/C_preprocessor"). ;)

---

### Post by Mozai on 2011-03-08
> **bodhi.zazen said:**
> 
LOL
No, simply use man


That doesn't answer any question that starts with the word 'why.'  Furthermore, laughing at someone who is asking a serious question is unprofessional.  I am surprised that someone with the title 'ubuntu forums admin' would be so disrespectful.

[QUOTE=sisco311]
You don't. cpp is not a dependency of bsdmainutils.
[/QUOTE]

It is a dependency of bsdmainutils, according to the package description I have.
```

moses@equius:~$ apt-cache show man-db |grep Depends:
Depends: groff-base (>= 1.18.1.1-15), bsdmainutils, 
 debconf (>= 1.2.0) | debconf-2.0, 
 dpkg (>= 1.9.0), libc6 (>= 2.8), 
 libgdbm3 (>= 1.8.3), zlib1g (>= 1:1.1.4)
moses@equius:~$ apt-cache show bsdmainutils |grep Depends:
Depends: libc6 (>= 2.4), libncurses5 (>= 5.6+20071006-3),
  bsdutils (>= 3.0-0), debianutils (>= 1.8), cpp

```

Thank you for pointing out that cpp is the preprocessor and not the compiler.  I feel better about installing it if it comes to that.  To satisfy my own curiosity, I think I'll build something small to replace /usr/bin/man

---

### Post by sisco311 on 2011-03-08
> **Mozai said:**
> 
It is a dependency of bsdmainutils, according to the package description I have.


Just checked it at [packages.ubuntu.com](http://packages.ubuntu.com/search?keywords=bsdmainutils&searchon=names&suite=all&section=all). It seems that they fixed the issue. In Natty [noparse](bsdmainutils (8.2.2))[/noparse], cpp is no longer a dependency of bsdmainutils:

```

sisco@acme:~$ apt-cache show bsdmainutils | grep Depends:
Depends: libc6 (>= 2.4), libncurses5 (>= 5.5-5~), bsdutils (>= 3.0-0), debianutils (>= 1.8)

```

---

### Post by Mozai on 2011-03-08
Groovy.  I love it when stuff is fixed/improved by the time I find it.

---

### Post by lithopsian on 2011-03-08
bsdmainutils includes all sorts of stuff.  Maybe one of those programs could can use a precompiler on its config file, something like that.  My guess would be calendar.  Maybe it used to and doesn't any more.

cpp is also needed by several other key packages, not least the tools used to start X.  You'll find it quite difficult to get a system that doesn't need it, although it can de done.

---

