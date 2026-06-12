---
title: "XGL with multiple users..."
date: 2006-06-04
forum: General Help
---

### Post by icksa on 2006-06-04
Hi:
I just installed XGL and its amazing, but I have one small problem.

I followed the wiki instructions, and everything went well, but when I log out and try to use XGL with another user I get an error which says the my session only lasted less than 10 seconds.

it says "fatal server error: server already running"

Basically whenever I restart, the first user to log in can use xgl/compiz, but the other user get an error...

Any Advice?

Thanks

---

### Post by icksa on 2006-06-04
Hi:
I figured out what was wrong...

I was following the ubuntu wiki page at:
[https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl)

It describes two methods for using XGL
Method A - Run xgl within and xorg server
and 
Method B - Run xgl on its own (as a replacement for xorg i guess)

I started using method A which produced the problem...switching to method B fixed everything

---

