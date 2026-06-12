---
title: "What's taking all my RAM?"
date: 2009-12-28
forum: General Help
---

### Post by TheNessus on 2009-12-28
40% taken on startup. no big program on. no broswer on. I should normally have 15% or so taken. Karmic, gnome, compiz on.

Any ideas? and how do I see exactly what's taking it all? sys monitor shows nothing should clog it that much and I should have minimal RAM taken up.

---

### Post by 45acp on 2009-12-28
You can type 'top' in the terminal and it will tell you what programs are running and how much of the cpu they are using.

---

### Post by BramWillemsen on 2009-12-28
I think this site answers your question, or maybe i misunderstood you. 

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by nmccrina on 2009-12-28
> **BramWillemsen said:**
> I think this site answers your question, or maybe i misunderstood you. 

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

:lolflag:

Thanks for posting, that was really interesting!

---

### Post by isecore on 2009-12-28
It's very simple - unused memory is wasted memory. Linux is very efficient and uses memory not allocated to applications for various caches, the disk-cache being the biggest.

---

