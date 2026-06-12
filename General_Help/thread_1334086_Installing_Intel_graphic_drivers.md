---
title: "Installing Intel graphic drivers"
date: 2009-11-22
forum: General Help
---

### Post by cel13 on 2009-11-22
I'm trying to install Xorg 2D drivers from this site:
[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

I have downloaded it, but I hvae problems compiling it, it says:
building should be as simple as:
$        ./autogen
$ make
$ sudo -c "make install"

But if I use autogen, I get: bash: ./autogen: No such file or directory

Could anyone please help ?

Thanks.
[B]
[/B]

---

### Post by Andreas1 on 2009-11-22
um, just to be on the safe side: you know you need to be in the directory where the script called "autogen" is? so, for example, if you extracted your software to home/yourname/Desktop/mynewsoftware you do:

```
$cd ./Desktop/mynewsoftware/
$ ./autogen
$ make
$ sudo -c "make install"
```

---

