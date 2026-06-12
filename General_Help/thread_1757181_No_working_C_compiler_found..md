---
title: "No working C compiler found."
date: 2011-05-13
forum: General Help
---

### Post by tomtomtomp on 2011-05-13
Hallo I am trying to compile x264 but ./configure returns just
> No working C compiler found.
Yes, I have installed build-essentials and yes, I have installed gcc :D
Already tried update and upgrade... so I dont know whats wrong :D my c++ compiler works normally.

Thanx for help :)

---

### Post by r-senior on 2011-05-13
I just downloaded it from here to try it:

[http://www.videolan.org/developers/x264.html](http://www.videolan.org/developers/x264.html)

I ran ./configure. It complained that I didn't have an assembler and suggested I ran ./configure --disable-asm. Then all seemed to compile OK.

How did you install gcc? From the repositories?

---

