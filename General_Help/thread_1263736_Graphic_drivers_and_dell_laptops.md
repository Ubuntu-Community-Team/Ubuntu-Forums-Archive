---
title: "Graphic drivers and dell laptops"
date: 2009-09-11
forum: General Help
---

### Post by jon.mithe on 2009-09-11
Hi,

Having some trouble getting graphics drivers working on a Dell Inspiron 6400.  Currently it is on the default drivers which are just slow, to the point things like iplayer / online TV do not run properly on fullscreen.

Tried installing fglrx but when I boot it crashes just before the login screen (the initial Ubuntu loader screen with progress bar comes up).  By crash, has black background then like miniature pixely repeating versions of the progress boot screens, with plenty of green + purple pixels

Unsure what I can try next, Can anyone help? 

On an install of 9.04 within windows parition.  I've installed it on my parents laptop to see if they can get along with it - which they are finding much better, just a handful of things to sort out before the change becomes a permanent one :)

Thanks,
Jon

---

### Post by Whiffle on 2009-09-11
Which video card does it have?

---

### Post by jon.mithe on 2009-09-11
hmm lol, could of swore this had a card but it looks like its just intel integrated graphics. Is there anyway I can improve this so it can handle fullscreen video?

---

### Post by StuartN on 2009-09-11
> **jon.mithe said:**
> Is there anyway I can improve this so it can handle fullscreen video?

It is probably an ATI Radeon Mobility x1400 and also probably uses some system RAM for graphics. Type "lspci" to list all PCI devices or "lshw -C video" to list all video hardware and look for the VGA controller. Type "free" and subtract the available memory from how much is actually installed to see how much the video is using.

In answer to the question of displaying fullscreen video, you might benefit from more memory if the available memory is below 1 gb. You would probably get an immediate speed boost from Ubuntu 8.10 or earlier - just boot from a live cd and play some video. "glxgears" will give a simple indication of video speed that you could use to compare under Jaunty and Intrepid.

---

### Post by P4man on 2009-09-11
If it is indeed one with Integrated Intel® Media **Dec**elerator, then have a look here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

edit: if that scares you too much (and i wouldn't blame you), an easier but equally risky/potentially unstable solutioin is try out ubuntu 9.10 Karmic Alpha 5. 
Its a prerelease, but maybe it already works well enough for you (it does for me) :

[http://cdimage.ubuntu.com/releases/karmic/alpha-5/](http://cdimage.ubuntu.com/releases/karmic/alpha-5/)

It fixes a lot of performance issues with intel integrated graphics.

---

### Post by jon.mithe on 2009-09-11
Thanks for all your help :)

lshw -C video revealed:

```
the Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
```

Interesting link to the jaunty intel graphics thanks, by the sounds of it 9.10 may resolve this, tempted to do the alpha but this version is pretty much working, so I think I'll just wait till 9.10 comes out.

Thanks for all the help,
cheers, jon.

---

