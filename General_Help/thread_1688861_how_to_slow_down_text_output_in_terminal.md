---
title: "how to slow down text output in terminal?"
date: 2011-02-15
forum: General Help
---

### Post by darthpenguin on 2011-02-15
Hi All,

I'd like to write a script that invokes a gnome-terminal session which slowly reads out text like the phosphor screensaver (could be anything, a log file, ascii art, song lyrics, whatev) and then closes.

I can invoke a terminal using [gnome-terminal -e 'cat /var/log/dmesg'] but the output flies pass by too quickly. any way to slow it down?

I know it seems like an odd request but if anyone has a suggestion I'd love to hear it.

Thank You.

---

### Post by requeth on 2011-02-16
I've never heard of this being configurable, and I have looked into it in the past for live log reading. One thing you may be able to do is pipe out to more: | more. If you waited then a second or two and sent a &nbsp the screen should reload to the next page of data, but it wouldn't flow, just flip pages.

The only other way I've heard of this being possible is to royally screw up the video driver configuration, which will make the terminal crawl, but your users will lynch you.

---

### Post by gmargo on 2011-02-16
Google for "slowcat".  I found a C program and two Perl programs, but I haven't tried them.

[http://grox.net/software/mine/slowcat/slowcat.c](http://grox.net/software/mine/slowcat/slowcat.c)

[http://www.splode.com/~friedman/software/scripts/src/slowcat]("http://www.splode.com/%7Efriedman/software/scripts/src/slowcat")

[http://pleac.sourceforge.net/include/perl/ch01/slowcat](http://pleac.sourceforge.net/include/perl/ch01/slowcat)

---

### Post by darthpenguin on 2011-02-16
Thanks gmargo, I copied the slowcat.py and it works great. Honestly, I'm just using this as a prank. imagin a dozan terminals randomly opening and closeing reading out meaningless text and a few things like "Skynet global defence online." or "accessing FBI mainframe" maybe some ascii text of a skull and crossbones. that'll scare (or at least annoy) 'em. hey, gotta have some fun right? still, it seems like it just might be a useful feature for more practical applications.. maybe not.. oh, well. Thanks again.

---

