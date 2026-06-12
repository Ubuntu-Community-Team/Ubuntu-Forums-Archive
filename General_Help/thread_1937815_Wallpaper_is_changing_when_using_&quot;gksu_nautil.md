---
title: "Wallpaper is changing when using &quot;gksu nautilus&quot;"
date: 2012-03-08
forum: General Help
---

### Post by sojusnik on 2012-03-08
Hi,

I've stumbled across a weird (bug)? Everytime I open nautilus with root rights, f.i. with "gksu nautilus" or by the "nautilus-gksu" script, my wallpaper is changing to a default one. Additionally, it does take quiet a while for nautilus to load. I've never experienced such a behaviour prior to 11.10.

Is this a bug or a feature and how to solve it (if it's bug)?

Btw, typing:
> 
gksudo "nautilus --no-desktop $HOME"

is not a solution...

---

### Post by gldearman on 2012-03-08
Just to be clear: Nautilus is the program that normally draws your wallpaper, right? And you don't get this effect if you invoke Nautilus as a normal user without root privileges?

---

### Post by Frogs Hair on 2012-03-08
Try restarting nautilus using following and try again . ```
nautilus -q
```

---

### Post by sojusnik on 2012-03-09
> **gldearman said:**
> Just to be clear: Nautilus is the program that normally draws your wallpaper, right? And you don't get this effect if you invoke Nautilus as a normal user without root privileges?

You're totally right.

@Frogs Hair

When invoking nautilus with gksu, the system freezes for nearly 20 seconds, then nautilus with root rights is opened. Your suggested command doesn't have an effect at all. The wallpaper stays, the only way I've found is to reboot ubuntu...

---

### Post by sudodus on 2012-03-09
> **sojusnik said:**
> You're totally right.

@Frogs Hair

When invoking nautilus with gksu, the system freezes for nearly 20 seconds, then nautilus with root rights is opened. Your suggested command doesn't have an effect at all. The wallpaper stays, the only way I've found is to reboot ubuntu...

I had a similar problem, when I ran nautilus via ssh from another computer, and then my solution was
```
gksudo "nautilus --no-desktop"
```
I tested it now; it works for me without a long delay. Are you running it via a remote connection from a desktop without nautilus installed? Or are you running it within a desktop environment which includes nautilus?

---

### Post by CatKiller on 2012-03-09
Tell root's nautilus not to draw the Desktop. There are probably neater ways to do it, but gksudo gconf-editor should suffice.

---

### Post by sojusnik on 2012-03-10
> **sudodus said:**
> I had a similar problem, when I ran nautilus via ssh from another computer, and then my solution was
```
gksudo "nautilus --no-desktop"
```
I tested it now; it works for me without a long delay. Are you running it via a remote connection from a desktop without nautilus installed? Or are you running it within a desktop environment which includes nautilus?

I'll stick to this workaround, as it seems to work fine, with no delays, and my wallpaper stays :)

---

### Post by Ender985 on 2012-05-29
I have the same issue, when gksu nautilus is invoked, the wallpaper changes to the (ugly) default, and whatever you do it stays until logoff. Using nautilus --no-desktop obviously works, but it is a ugly workaround to have to alias that.

More importantly, I suspect gksu gets stuck in sudo mode after that. I can gksu gedit and the likes without having to answer any other password prompts, even after having waited 10 minutes (!) from the initial gksu. This looks like a big security flaw that should be patched asap!

---

### Post by sudodus on 2012-05-31
> **Ender985 said:**
> ...

More importantly, I suspect gksu gets stuck in sudo mode after that. I can gksu gedit and the likes without having to answer any other password prompts, even after having waited 10 minutes (!) from the initial gksu. This looks like a big security flaw that should be patched asap!

You may be right but I have not noticed that! I know there is a time-out for sudo, but it might be more than 10 minutes, probably less than one hour in Ubuntu. This can vary between distros. Maybe you can test it with [FONT="Courier New"]gksudo nautilus[/FONT] running and *not* running.

While you have a superuser's nautilus session running, you have power to a lot to the system, so that is probably the biggest risk. My advice is to close it as soon as the particular task (requiring privileges) is finished.

---

