---
title: "Matlab doesn't start"
date: 2011-08-26
forum: General Help
---

### Post by lobo_20 on 2011-08-26
I've just installed MatlabR2010b on natty following this tutorial:

[http://jonon.gs/blog/math/how-to-install-matlab-on-ubuntu-linux/](http://jonon.gs/blog/math/how-to-install-matlab-on-ubuntu-linux/)

No problems there, I created the launcher, double clicked it, got the matlab starting window and then... nothing... no matlab desktop, nothing...

I tried to start it from the terminal and I got the "libc.so.6 not found" message, fix it with this:

[http://morganbye.net/blog/2011/05/matlab-ubuntu-1104](http://morganbye.net/blog/2011/05/matlab-ubuntu-1104)

Tried running matlab again with my launcher and the terminal to no avail... all I get is the starting window... :S

can somebody help me please?

Thanx in advance :)

EDIT 

The problem is solved :D

I was missing the matlab specific bin directory

> mkdir ~/.matlab/bin

and finally the preferences permission

> sudo chown -R ${USER}:${USER} ~/.matlab

Now Matlab is running smoothly :P

Excuse me for bothering you all

---

