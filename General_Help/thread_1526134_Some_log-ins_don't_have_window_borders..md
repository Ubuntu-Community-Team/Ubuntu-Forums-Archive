---
title: "Some log-ins don't have window borders."
date: 2010-07-07
forum: General Help
---

### Post by Roasted on 2010-07-07
Sometimes when I boot up and log in, I have no window borders. The entire area with min/max/close is just gone. If I log out and back in, most times it comes back. What gives?

---

### Post by Roasted on 2010-07-16
upppppp

---

### Post by Roasted on 2010-08-16
uppppp

---

### Post by hawthornso23 on 2010-08-16
Those things are called window decorations (I don't know why - they are not very decorative). A quick fix for this common problem is to restart your window manager. Either 

```
compiz -replace ccp 
```

or 

```
metacity -replace
```

Will do the job depending on which window manager you use.

I have keyboard shortcuts associated to those two commands so I can turn compiz on and off quickly with minimal fuss. 

To go beyond this bandaid you need to find out what is causing the problem. Simplify your compiz settings if you are using compiz and make sure you are not using plugins you really don't need. I found I had the goldfish plugin selected even though I had an opaque cube. Deselecting this made compiz more responsive and stable and I haven't lost window decorations since.

---

### Post by stinkeye on 2010-08-17
> Sometimes when I boot up and log in, I have no window borders
I get this sometimes as well.

Alt+F2 and run
```
gtk-window-decorator --replace
```

Using fusion-icon (search in software centre) allows you to easily change 
or reload your window manager or window decorator.

---

### Post by neigun on 2010-09-13
Hi Guys

Has anyone found a permanent solution to the lack of window decorations?

I've tried removing Compiz from my system but booted up to no window decs](*,) The same happens if I use Metacity or Compiz.

All the solutions only seem to provide a temporary fix until a reboot.

Does anyone know why it happens?  Just prior to this problem I had upgraded my Chromium browser from a ppa. I've now completely removed it from my system, but the problem still occurs- doh!

System specs include:

10.04 64 bit
ATI 3650 AGP

Neil

---

