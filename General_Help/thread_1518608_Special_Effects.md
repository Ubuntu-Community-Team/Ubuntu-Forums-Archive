---
title: "Special Effects?"
date: 2010-06-26
forum: General Help
---

### Post by CrusaderAD on 2010-06-26
Are special effects not available with the netbooks? They're all grayed out.

---

### Post by Sonsum on 2010-06-26
No, visual effects are definitely available. My Samsung N120 netbook is fully usable with compiz. (And believe me, I use a lot of eye candy).

What netbook do you have?

---

### Post by CrusaderAD on 2010-06-26
It's an Asus eee pc.

---

### Post by Sonsum on 2010-06-26
Try this:
```
sudo aptitude install compiz-gnome
```

Hopefully, that'll work for you.

---

### Post by CrusaderAD on 2010-06-26
Hm, I'll try it just as soon as my updates are done... you think compiz isn't installed?

---

### Post by Sonsum on 2010-06-26
It could be. I found a thread with someone who had a similar problem and that seemed to fix it.

I don't remember having to install compiz on my netbook :-k

---

### Post by themusicalduck on 2010-06-26
They aren't compatible with the netbook edition I think. If you have that installed then I'm fairly sure you can't use them. You can with the desktop edition though.

---

### Post by Sonsum on 2010-06-27
> **themusicalduck said:**
> They aren't compatible with the netbook edition I think. If you have that installed then I'm fairly sure you can't use them. You can with the desktop edition though.

Very untrue. Everything works with compiz by default on my netbook except for the cube cause UNR doesn't allow workspaces.

It can be done. I've done it.

---

### Post by Yarui on 2010-06-27
> **themusicalduck said:**
> They aren't compatible with the netbook edition I think. If you have that installed then I'm fairly sure you can't use them. You can with the desktop edition though.
I have never used the netbook edition, so I may be wrong, but I'm pretty sure everything that is compatible with the desktop edition is also compatible with the netbook edition so long as your hardware supports it.  The only difference between the two is the stuff that comes with it by default.  The netbook edition is the same OS optimized for use on netbooks.

---

### Post by CrusaderAD on 2010-06-27
> **Sonsum said:**
> Try this:
```
sudo aptitude install compiz-gnome
```

Hopefully, that'll work for you.

That did it! Strange it wasn't there by default, but oh well! Easy Fix! :)

---

### Post by CoreyB. on 2010-06-27
Can you actually notice that the compiz effects are on?  I was under the impression that the netbook interface wouldn't use the compiz effects, hence not installed by default, and on each reboot the effects are turned off.  Is this true?

---

### Post by Yarui on 2010-06-27
> **CoreyB. said:**
> Can you actually notice that the compiz effects are on?  I was under the impression that the netbook interface wouldn't use the compiz effects, hence not installed by default, and on each reboot the effects are turned off.  Is this true?
Regardless of whether or not it is installed by default the program will be turned off every time you shut down.  To avoid having to start up compiz every time you turn your computer on you just have to make it a startup program.  Any program can be made to start with the machine, the desktop edition just has compiz as a default startup application.

---

### Post by Sonsum on 2010-06-27
Yay! I'm glad that worked. 

And I'm not sure where everyone's getting the idea that netbooks can't use compiz. 

Have you guys been talking to Microsoft? Because Aero is removed from the netbook edition of Windows 7. Very annoying :mad:

---

### Post by CoreyB. on 2010-06-29
But using the netbook interface, can you visually tell that desktop effects are on?

---

### Post by Sonsum on 2010-06-29
> **CoreyB. said:**
> But using the netbook interface, can you visually tell that desktop effects are on?

Yup. Windows wobble, I can paint fire on the screen. The minimize effects may not work, I can't remember.

I realized after a while that the normal gnome desktop works perfectly fine for a netbook and have used that ever since.

---

