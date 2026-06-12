---
title: "Opera YouTube player not responsive - SWFDec"
date: 2010-06-19
forum: General Help
---

### Post by chroncile on 2010-06-19
Hi, I have installed Opera on Ubuntu 10.04 and I installed SWFDec as well. When I watch YouTube videos that use the old YouTube player, the controls do not work. The controls work with the new YouTube player.

This does not happen on FireFox. What should I do to fix the problem?

---

### Post by lovinglinux on 2010-06-20
Don't use swfdec.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If you are using a 64bit browser, then do the following to fix the issue with the buttons.

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by chroncile on 2010-06-20
I did all that, but nothing actually changed in Opera.

---

### Post by lovinglinux on 2010-06-21
> **chroncile said:**
> I did all that, but nothing actually changed in Opera.

Type **opera[noparse]:[/noparse]plugins** in the address bar, copy the path to the Shockwave Flash plugin and paste here.

---

### Post by chroncile on 2010-06-21
```
/usr/lib/flashplugin-installer/libflashplayer.so
```

---

### Post by lovinglinux on 2010-06-21
So, it does play the videos, but you can't click the buttons, is that right?

Can you click the buttons with Firefox or Chrome?

---

### Post by radddi on 2010-06-21
What's your Opera version? Nonresponsiveness of the Youtube player used to be a problem I think in version 10.10 and some of the early 10.60 alphas. If you are still running 10.10 I would strongly recommend you switch to the new Opera 10.60 Beta. It's unbelievably stable, ridiculously fast compared to older versions and it has extensive support for HTML5 and can even play WebM videos in Youtube.

[http://www.opera.com/browser/next/](http://www.opera.com/browser/next/)

.:CheerS:. :popcorn:

PS: No, seriously, I'm not advertising the browser. I just liked the new versions so much that for the first time in my life I actually fully migrated to an ALPHA version!!! And it worked and still works flawlessly.

---

### Post by chroncile on 2010-06-21
Yes, that fixed it raddi. Thank you :)

---

