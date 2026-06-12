---
title: "Startup free memory (10.04 Lucid)"
date: 2010-04-21
forum: General Help
---

### Post by bigsmitty64 on 2010-04-21
Ran free m in terminal at **fresh** startup. 
I have 2 gigs of ram.
This says Ubuntu is using over 1/2 a gig at startup right? That doesn't seem right to me.I checked it out because it seems like I'm getting high memory usage and I can't figure out what is causing it. I think some it is firefox though.I was in firefox (3.6.3) and the drop down menues were acting weird (transparent until hovering over them) And the title bar would disappear completely,forcing a restart of the browser. Think I'll try Chromium for a while.
But my original question is: Is this normal mem usage at startup in Lucid?

```
marshall@marshall-desktop:~$ free m
             total       used       free     shared    buffers     cached
Mem:       2056696     606820    1449876          0      35336     229196
-/+ buffers/cache:     342288    1714408
Swap:      6023160          0    6023160

```

If someone wants to move this to Lucid testing feel free, I just realized I should've posted there :(

---

### Post by taqkavar on 2010-04-21
Nah, it doesn't have anything to do with lucid. out of that ~ 600 Mb, about 350 Mb is used for caching, basically thats the kernel loading stuff in advance in case you need them, it frees it up as soon as you need the space.
 
> ```
-/+ buffers/cache:     342288    1714408
```

So no its okay, don't know whats the deal with Firefox thought.

---

### Post by bigsmitty64 on 2010-04-21
I downloaded Chromium and am trying it out.  So far so good. The thing is, firefox has been acting weird since I started with Lucid (64 bit). with the strange menu actions and I noticed on youtube for example, the area under a video (description area) is grayed out when you scroll up and down. All in all, I haven't been real happy with firefox lately even when I was using windows. Just seems after a while it eats up mem. It would easily be at 6 or 700 megs after a half hour or so with a few tabs open (by few I mean 2 or 3) 
I'll try out Chromium for a while and see how that goes.

---

### Post by john newbuntu on 2010-04-21
If you have a problem with 3.6.3, try their daily ppa for lucid
[http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) lucid main

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

