---
title: "gnome settings daemon uses 3GB of RAM"
date: 2011-04-09
forum: General Help
---

### Post by serenti on 2011-04-09
Hi, 

The gnome settings daemon on my computer uses an insane amount of RAM, every few days it reaches about 3GB and when it does, everything freezes to the point that I need to hard-reset the computer. Can't even kill the process. This makes Ubuntu very hard to use.

I saw a lot of questions concerning this on different forums but no solution so far.

Any ideas what's causing it and how to fix it? Thank you for any suggestions you might have. (Ubuntu 10.10 64bit)

Tito

---

### Post by techunit on 2011-04-09
Never had that problem. I have run into mem problems with chromium but never anything with Gnome.

Hardware? Software? Gnome Desktop (I assume so) Any Custom Kernels?

---

### Post by serenti on 2011-04-10
No, nothing custom, just a standard Ubuntu 10.10 running on software mirror raid 2x2GB 4GB RAM, AMD Phenom. I use it for web development, so I have apache/mysql/php/cyrus running on it. When I start the computer, gnome-settings-daemon uses 19MB, then it slowly keeps growing until after several days it can grow to nearly 3GB (I suspend the computer for the night instead of shutting it down). Oh, and I use the picture slideshow screensaver (the one included in gnome) - maybe that has something to do with that, maybe I should try turning it off.

When I ran a google search on this I found a lot of people reporting this error as a memory leak bug, the earliest posts being from 2007. I find it hard to believe that it wouldn't have been fixed yet if it's an actual bug.

I'm hoping there's someone out there who found a solution to this.

---

### Post by serenti on 2011-04-10
Oh, and I use a customized Clearlooks theme instead of the default one. It's a settings daemon, maybe it has something to do with the theme and the screensaver I use...

---

