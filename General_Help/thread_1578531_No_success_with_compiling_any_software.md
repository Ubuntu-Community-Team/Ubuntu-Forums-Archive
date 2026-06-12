---
title: "No success with compiling any software"
date: 2010-09-20
forum: General Help
---

### Post by mpw on 2010-09-20
Hallo,

I'm using Ubuntu since Version 8.4(using 10.04-64bit right now) and I start feeling advanced instead of absolute beginner. But I still can't compile anything.

In many boards many people show how easy it is to compile your own programs from source. I had never success with this.

I want to compile gummi 0.5 from [http://gummi.midnightcoding.org/?page_id=6](http://gummi.midnightcoding.org/?page_id=6) as there is no deb for ubuntu yet. It will arrive soon, that's not the point, but I cant to become capable of compiling my own programme.

What I did:

I installed the build-essential, downloaded the sources, unpacked them. But already ./configure from in the source-folder just fails.
```
configure: error: You need Glib >= 2.16.0 to build gummi

```Ok, no problem. Went to here and dowloaded glib 2.24
[http://ftp.gnome.org/pub/gnome/sources/glib/2.24]("http://ftp.gnome.org/pub/gnome/sources/glib/2.24/")

But trying to compile that one, I get:
```
configure: error: *** Working zlib library and headers not found ***

```And this is not the only software it runs like this. Just anything I try, doesn't work.

Could you help me trough this. I'd really like to learn this.

Thanks for hints.

Bye
MPW

---

### Post by Claus7 on 2010-09-20
Hello,

I do not think that maverick does not have that version of glib you are looking for. As a result you would be able to install it right away from synaptic and save yourself from solving dependency problems.

If you want to install a program yourself, based on packages that are not by default installed on your system, then you might have to compile for a long time. And the thing is becoming more difficult if you find double (not remember exactly the name) dependency problems where two libraries need simultaneously one another so as to work.

Be patient and start with programs less dependent on  extra packages.

Regards!

---

### Post by nothingspecial on 2010-09-20
```
 sudo apt-get install cdbs debhelper autotools-dev libgtk2.0-dev libglib2.0-dev libpoppler-dev libpoppler-glib-dev libgtksourceview2.0-dev libgtkspell-dev libgtk2.0-0 libglib2.0-0 libgtksourceview2.0-0 libgtkspell0 libpoppler5 libpoppler-glib4
```

See if that get`s you going :) Although, knowing me there is probably a typo.

---

### Post by mpw on 2010-09-20
> **nothingspecial said:**
> ```
 sudo apt-get install cdbs debhelper autotools-dev libgtk2.0-dev libglib2.0-dev libpoppler-dev libpoppler-glib-dev libgtksourceview2.0-dev libgtkspell-dev libgtk2.0-0 libglib2.0-0 libgtksourceview2.0-0 libgtkspell0 libpoppler5 libpoppler-glib4
```See if that get`s you going :) Although, knowing me there is probably a typo.


Thanks! I just compiled my first programm. And it starts!

A new level has just begun.

---

### Post by nothingspecial on 2010-09-20
Excellent :)

---

