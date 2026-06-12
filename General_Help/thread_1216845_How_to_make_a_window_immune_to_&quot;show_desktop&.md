---
title: "How to make a window immune to &quot;show desktop&quot;"
date: 2009-07-18
forum: General Help
---

### Post by roccivic on 2009-07-18
I wonder if it is possible to make a window, say "gnome-terminal", immune to "show desktop".
That is, when I hit the "show desktop" button I don't want "gnome-terminal" to be minimized.

I'm running Gnome 2.22.3 on Hardy.

Many thanks for any help.

```
roccivic@roccivic-pc:~$ uname -r
2.6.24-24-generic
roccivic@roccivic-pc:~$ compiz --version
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.4
```

---

### Post by LightningCrash on 2009-07-18
There's a program called Devilspie that might do what you want.

[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

It's in the repos as devilspie.

---

### Post by CatKiller on 2009-07-18
If you're using Compiz, you can use CompizConfig Settings Manager &#8594; Desktop &#8594; Show Desktop &#8594; Misc. Settings &#8594; Window Types to tell the plugin to ignore any window whose Name is gnome-terminal.

---

### Post by roccivic on 2009-07-19
> **CatKiller said:**
> If you're using Compiz, you can use CompizConfig Settings Manager &#8594; Desktop &#8594; Show Desktop &#8594; Misc. Settings &#8594; Window Types to tell the plugin to ignore any window whose Name is gnome-terminal.

I tried this, but it does not work. I replaced the default options ```
type=toolbar | type=utility | type=dialog | type=normal
``` for "show desktop" in ccsm with ```
!(name=gnome-terminal)
```
But all gnome-terminal windows are still hidden :( The only thing that changed is that the gnome-terminal windows disappear immediately, but all other windows are faded out of the screen with an animation effect.

---

### Post by roccivic on 2009-07-19
Just read manual, it may just do what I need, thanks.

> **LightningCrash said:**
> There's a program called Devilspie that might do what you want.

[http://burtonini.com/blog/computers/devilspie](http://burtonini.com/blog/computers/devilspie)

It's in the repos as devilspie.

---

### Post by CatKiller on 2009-07-19
You're right. The other windows get affected by the Show Desktop plugin and the gnome-terminal window doesn't, but the gnome-terminal window still gets minimised by the (almost equivalent) "hide all normal windows and set focus to the desktop background" keyboard shortcut. That's annoying. I haven't yet been able to find a way to fix that. The only thing I can think of is to stop the gnome-terminal window counting as "Normal," but I don't know how to do that.

---

### Post by roccivic on 2009-07-19
I had a good look into devilspie and tried it, too. But it just looks like it cannot do what I need it to.


I downloaded the source code for "gnome-panel" and had a little look into the "show desktop" applet code. I guess I could modify the applet, then recompile and reinstall it, but I would really like to find a less intrusive way of doing what I want...

---

### Post by quazi on 2009-10-26
> **roccivic said:**
> I had a good look into devilspie and tried it, too. But it just looks like it cannot do what I need it to.


I downloaded the source code for "gnome-panel" and had a little look into the "show desktop" applet code. I guess I could modify the applet, then recompile and reinstall it, but I would really like to find a less intrusive way of doing what I want...

If you found a solution for this I'd like to hear it.  I'm annoyed by having rainlendar and sticky notes get minimized when I use the "Show Desktop" shortcut.  I'm showing the desktop so I can see them!

---

### Post by bartaz on 2009-11-04
> **roccivic said:**
> I had a good look into devilspie and tried it, too. But it just looks like it cannot do what I need it to.


I was able to make devilspie do that.

In my case it was Tilda that I wanted to stay visible when I show desktop. Here is a devilspie config to do that:
```
(if
(is (window_class) "Tilda")
(begin
(wintype "dock")
)
)
```

Of course you can use any window selector you want.
Here is a great overview of what can be done with devilspie:
[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)

The key here is changing window type to "dock".
```
(wintype "dock")
```
"Dock" windows do not hide on "show desktop".

You can also change window type to "desktop" to make it stick to the desktop (under any other windows, even when focused).

---

### Post by bartaz on 2009-11-04
> **bartaz said:**
> 
The key here is changing window type to "dock".
```
(wintype "dock")
```


Unfortunately changing window type to "dock" gives it completely other treatment by window manager. It won't have decoration (window border and title bar), it won't be movable, etc.

While it's quite fine with Tilda, that is a 'dock-type' terminal window, it may not be good if you want to use it with normal windows.

The biggest problem I found with using "dock" window type is being unable to get the keyboard focus by clicking window, which make it approach simply useless for terminal windows.

But it should still be fine for some notes or other widget-like windows.

---

### Post by mwguthrie on 2010-03-20
First of all, sorry for bumping an old topic, but I've found a solution. Unfortunately, it requires the use of compiz-fusion. For example, if one would like their screenlets to remain immune to the effects of the "show desktop" keyboard shortcut...

Open gconf-editor and avigate to /apps/compiz/general/allscreens/options and uncheck "hide_skip_taskbar_windows".

I have yet to observe any annoying unintended effects from this alteration. Let us hope there are few.


EDIT: This also applies to any window in the screenlets plane.

---

### Post by estyles on 2010-03-23
Great timing mwguthrie, was just trying to figure this out!  Works very well with using compiz to create a transparent desktop console.

---

### Post by J V on 2010-07-04
Awesome, was looking for this forever, now my desktop is aweSOOOOME!

---

