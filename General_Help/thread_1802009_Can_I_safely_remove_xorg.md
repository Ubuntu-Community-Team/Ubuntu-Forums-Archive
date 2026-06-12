---
title: "Can I safely remove xorg"
date: 2011-07-11
forum: General Help
---

### Post by varx on 2011-07-11
PROBLEM: My computer has an nvidia video card. I'd like to remove the packages that support ati and radeon. When I try to remove xserver-xorg-video-ati or xserver-xorg-video-ati, the package manager wants to remove xserver-xorg-video-all. 

QUESTION: Is it safe to remove xserver-xorg-video-all? Obviously, I want to keep support for my nvideo card.

Thanks.

---

### Post by snowpine on 2011-07-11
Welcome to the forums! There is no benefit to removing the ati and radeon drivers. Drivers that aren't needed are not loaded into RAM and have no impact on performance. :)

---

### Post by varx on 2011-07-11
Thanks, snowpine. If those files are pretty small (I haven't checked), I guess that's fine. Otherwise, though, I'm trying to pare down my Ubuntu installation, since I've installed to an SSD with limited space.

---

### Post by snowpine on 2011-07-11
If you're *very* low on SSD space (I've successfully installed Ubuntu 11.04 on a tiny little 8gb SSD!) then your best option is to start with a minimal install and build up, rather than start with a full install and strip down.

Here's a good how-to:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

A few other ultra-minimalist distros I can recommend include Arch, Puppy, SliTaz, and TinyCore. (I've actually run SliTaz off of a 128mb thumb drive!)

---

### Post by 3Miro on 2011-07-11
xserver-xorg-video-all should be a meta package. That means a package that simply installs other packages and doesn't do anything by itself. It should be safe to remove it. Just remember the command:
```
sudo apt-get install xserver-xorg-video-all
```
in case you lose your graphical environment.

The title of the thread is also misleading. If you remove xorg itself, then you will lose your graphics.

---

### Post by varx on 2011-07-11
> **3Miro said:**
> xserver-xorg-video-all should be a meta package. That means a package that simply installs other packages and doesn't do anything by itself. It should be safe to remove it. Just remember the command:
```
sudo apt-get install xserver-xorg-video-all
```in case you lose your graphical environment.

The title of the thread is also misleading. If you remove xorg itself, then you will lose your graphics.
Thank you, 3Miro. I fixed the thread title, too.

---

### Post by varx on 2011-07-11
> **snowpine said:**
> If you're *very* low on SSD space (I've successfully installed Ubuntu 11.04 on a tiny little 8gb SSD!) then your best option is to start with a minimal install and build up, rather than start with a full install and strip down.

Here's a good how-to:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Starting small and building up is a good suggestion. I've already done it the other way, though, so I'll live with what I've got until I decide to do a fresh install later on. I expect I'll want to do that at some point, anyway. My SSD space isn't extremely limited, and I have a second spinning-platter HD that can keep data on. The truth is, I just don't like the idea of having unnecessary packages taking up space. I'll probably feel that way even when SSDs are measured in terrabytes.

---

### Post by sanderd17 on 2011-07-11
If you really want to use as less space as possible, than Ubuntu is not your distro. The main goal of Ubuntu is to work out of the box. So all drivers have to be there. 

A minimal distro (like the ones snowpine mentioned) could help you more (if you have the guts to take every decision). I would certainly advise Puppy if you want something graphical that uses a minimum of space and still has a lot of packages to install, and Arch if you want to create your system from the bottom up, helped by the Arch community and their wonderful amount of up to date packages.

If you go for a very minimal Linux (like DSL or SliTaz), than you will have no package manager either.

---

### Post by Bucky Ball on 2011-07-11
Working backwards is hard graft if you're looking to strip it down. You'll never get close to bare-bones or minimal. But you'll probably learn plenty along the way so welcome and have fun! ;)

The minimal install gives you the option of *only installing the hardware drivers you need* to the hard drive (or SSD) right from the get-go, which sounds like exactly what you want. Compiling your own kernel (which you can do within the Ubuntu environment) is even better. I would perhaps lean toward treating your current install as learning the ropes, getting familiar with Ubuntu, and a warm-up for the future minimal. It is not overly complicated procedure but you do want to have a good idea about Ubuntu before attempting it ('specially compiling a kernel, although that is not overly difficult once you have some idea either). 

Enjoy the learning curve!

---

### Post by snowpine on 2011-07-11
> **sanderd17 said:**
> If you go for a very minimal Linux (like DSL or SliTaz), than you will have no package manager either.

SliTaz has a **wonderful** package manager (tazpkg). I think DSL used standard Debian package management before it became **obsolete** years ago. :)

---

### Post by Bucky Ball on 2011-07-11
> **sanderd17 said:**
> 

If you go for a very minimal Linux (like DSL or SliTaz), than you will have no package manager either.

If you go for a proper minimal install (not a 'minimal' Linux) you get no package manager; you install the one you want, and the desktop environment you want, and the package manager, etc ... A minimal install installs only what you need to get your machine breathing, little else, unless you tell it to.

---

