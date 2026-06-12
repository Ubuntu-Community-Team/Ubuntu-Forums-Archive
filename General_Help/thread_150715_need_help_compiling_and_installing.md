---
title: "need help compiling and installing"
date: 2006-03-26
forum: General Help
---

### Post by sr243 on 2006-03-26
I am testing out linux, and am having some troubles compiling software.

I am trying to get the software from
[http://www.geocities.com/Colosseum/Loge/6333/](http://www.geocities.com/Colosseum/Loge/6333/)

The link on that site to the precompiled version
[http://www.geocities.com/Colosseum/Loge/6333/xsg32_linux.zip](http://www.geocities.com/Colosseum/Loge/6333/xsg32_linux.zip)
doesnt seem to work for me.

The link to the source code
[http://www.geocities.com/Colosseum/Loge/6333/xsg3_1_tar.gz](http://www.geocities.com/Colosseum/Loge/6333/xsg3_1_tar.gz)
doesnt work either.

I have all the needed packages to compile from the build-essential package, but it keeps giving me a long string of errors.

Could anyone try to get this thing to work?  Thanks!

(Basically, my dad likes to play this game and refuses to let me keep linux on this machine without this game.)

---

### Post by Ramses de Norre on 2006-03-26
Did you read the read_me?
Can you give some more details, which command did you execute and what error did you get?

---

### Post by sr243 on 2006-03-26
i did read the readme.
I followed its instruction:

"make -f Makefile.simple"

the error list is long, but it starts with:

cc -O -c auxf.c
auxf.c: In function &#8216;fatal_error&#8217;:
auxf.c:122: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
cc -O -c deploy.c
cc -O -c event_handler.c
event_handler.c:11:22: error: X11/Xlib.h: No such file or directory
event_handler.c:12:27: error: X11/Intrinsic.h: No such file or directory
event_handler.c:13:24: error: X11/keysym.h: No such file or directory
In file included from event_handler.c:21:
struct.h:33: error: syntax error before &#8216;XColor&#8217;

Did you get it to work, Ramses?

---

### Post by halitech on 2006-03-26
I tried it as well, not that I'm much of an expert and I got the exact same messages

---

### Post by sr243 on 2006-03-26
thanks for the effort halitech.
man, i really really want to get this to work =[

---

### Post by sr243 on 2006-03-26
what am i doing wrong? gah...

---

### Post by sr243 on 2006-03-28
i'd hate to go back to windows, but that's the only option unless i can get this stupid thing to work...

---

### Post by dmizer on 2006-03-28
this part of your error:
> event_handler.c:11:22: error: X11/Xlib.h: No such file or directory
event_handler.c:12:27: error: X11/Intrinsic.h: No such file or directory
event_handler.c:13:24: error: X11/keysym.h: No such file or directory
is telling you that your trying to compile something that needs dependencies that you don't have.  specifically Xlib.h Intrinsic.h and keysym.h ... you can probably get those through synaptec or apt-get.

the down side of compiling your own package is that you need to carefully look at your error and determine where things went wrong.  they're often dependency related.

---

