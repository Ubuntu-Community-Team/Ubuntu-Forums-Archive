---
title: "Zlib required to compile from source"
date: 2009-11-29
forum: General Help
---

### Post by blueshiftoverwatch on 2009-11-29
I'm trying to compile an app from source and when I get to the ./configure stage it won't let me progress any farther because it says I need Zlib 1.2.3.

I went into Synaptic and the package "zlib1g" is already installed.

Just to make sure that I have everything that I needed I checked to make sure the build-essential, automake, and checkinstall packages were also installed. Which they were.

---

### Post by Leppie on 2009-11-29
try to install the development package:
```
$apt-get install zlib1g-dev
```

Often development libraries are needed for compilation from source.
Hope this helps

---

### Post by blueshiftoverwatch on 2009-11-30
> **Leppie said:**
> try to install the development package:
```
$apt-get install zlib1g-dev
```

Often development libraries are needed for compilation from source.
Hope this helps
That helped. But now that I made it past that error I got another error:
```
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
```
I checked Synaptic for "curses" but there were either for perl or some language called "Yorick".

---

### Post by snova on 2009-11-30
> **blueshiftoverwatch said:**
> That helped. But now that I made it past that error I got another error:
```
checking for initscr in -lcurses... no
checking for initscr in -lncurses... no
checking for initscr in -lpdcurses... no
configure: error: A curses library is required to use the debugger
```
I checked Synaptic for "curses" but there were either for perl or some language called "Yorick".

Install the **ncurses-dev** package.

---

### Post by blueshiftoverwatch on 2009-11-30
Thanks for the help both of you.

Why wouldn't it tell me the exact name of the packages I needed instead of making me try and guess it myself?

Although after all that apparently even when compiled from source the app I'm trying to install doesn't support 64 bit CPU's. I was under the impression that almost any 32 bit app could be made to run on a 64 bit system as long as you had the source code and compiled it yourself.

After a quick search I found a [guide]("http://ubuntuforums.org/showthread.php?t=588744&highlight=dfreer+zsnes") on how to get Zsnes to work on a 64 bit computer which I'll have a look at tomorrow. If that doesnt' work, I'll try Bsnes.

---

### Post by snova on 2009-11-30
> **blueshiftoverwatch said:**
> Why wouldn't it tell me the exact name of the packages I needed instead of making me try and guess it myself?

Perhaps when you searched on "curses", it tried to match whole words. I just happen to know that the implementation of curses used on Linux is called ncurses (and configure knows this, it checked for both, as well as another variant).

> Although after all that apparently even when compiled from source the app I'm trying to install doesn't support 64 bit CPU's. I was under the impression that almost any 32 bit app could be made to run on a 64 bit system as long as you had the source code and compiled it yourself.

I don't know, though I think that should usually hold true. However, emulators tend to do unusual things with the CPU, especially if they do more than simply interpret instructions (recompiling to native code, for example).

---

