---
title: "Alien Arena 2006 Gold Edition for Linux won't work...  can't find libgtk-1.2.so.0"
date: 2011-06-29
forum: General Help
---

### Post by t0p on 2011-06-29
Back in 2007 I got a cover CD off a Linux mag, which included a game called Alien Arena 2006 Gold Edition for Linux.  It was a nice game (1st person shoot-'em-up like Quake and Doom) and I'd like to play it again.  Unfortunately I lost the CD.

Alien Arena is in Synaptic.  But when I install it, I can't get it to work.  The mouse pointer will not work in the game menu window, arrow keys don't work... I get some music, but that's about it.  I figure maybe it won't work because the new, improved Alien Arena won't play nice with my computer (Intel Pentium 4 CPU 1.70 GHz, the very same computer I used in 2007,  but now with added RAM - 1GB instead of 256MB) so I ooked for the 2006 gold edition I knew and loved before.

A little googling turned up the original game - alienarena-2006ge-x86.run.  But when I try to run it, I get a little window saying:

> 
Alien Arena 2006: Gold Edition for Linux

Verifying archive integrity... All good
Uncompressing Alien Arena 2600: Gold Edition for Linux.............................

/home/t0p/.setup20181: error while loading shared libraries: libgtk-1.2.so.0; cannot open shared object file: No such file or direcctory
Press Return to close this window#I've tried to find this libgtk-1.2.so.0, but so far unsuccessfully - plus, even if I find it I don't know what I'm meant to do with it.

All I want is a nice 1st person shoot-'em-up that will work nicely on my computer.  It's worked before... but not any more.  Can anyone help?

Cheers.

---

### Post by t0p on 2011-07-21
bump...

---

### Post by CatKiller on 2011-07-21
> **t0p said:**
> I've tried to find this libgtk-1.2.so.0, but so far unsuccessfully - plus, even if I find it I don't know what I'm meant to do with it.

Bad form of them to need a particular version. You can get the .deb for libgtk1.2 from [here]("http://packages.ubuntu.com/hardy/libgtk1.2"). Install it in the usual way.

You're probably better off trying to get the version from the repositories working, though.

---

### Post by t0p on 2011-07-21
Boo hoo!  I downloaded **libgtk1.2_1.2.10-18.1build2_i386.deb **from that link.  But when I try to install it using gdebi I get the following:

> 
Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)


So I *still* can't play Alien Arena 2006 Gold Edition for Linux...

I've been playing freedoom for a while now, but it doesn't come anywhere near Alien Arena 2006.  And, as I wrote before, Newer versions of Alien Arena just  won't play on my oldy mouldy machine...

So what am I gonna do now???

---

### Post by CatKiller on 2011-07-21
> **t0p said:**
> I get the following:

```
 Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)
```
...
So what am I gonna do now???

As I said before, your best bet is to get the version in the repositories working. If you still insist on installing the earlier version, you can get .debs to satisfy the dependencies from the same place, or from the repositories.

---

### Post by t0p on 2011-07-22
I tried to play th version of Alien Arena in the repos.  But it obviously needs more oomph than my computer is capable of.  That's why I'm messing around with the 2006 version - I *know* the 2006 version works ok on my hardware as I used to play with it back in 2007.

Ah well, back to freedoom I guess...

---

### Post by CatKiller on 2011-07-22
> **t0p said:**
> it obviously needs more oomph than my computer is capable of.  
It's not obvious at all. Nothing you've posted so far suggests a performance issue. Running but really slowly means that your computer can't handle it. The symptoms you've described are buggy or misconfigured behaviour.

---

