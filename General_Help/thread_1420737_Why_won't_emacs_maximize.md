---
title: "Why won't emacs maximize?"
date: 2010-03-03
forum: General Help
---

### Post by lykwydchykyn on 2010-03-03
I've been using emacs for over a year now, and this has been bugging me for a while; Google turns up no answers, so I thought I'd ask.

When running emacs-gtk under KDE, I cannot maximize emacs.  If I click "maximize", the window expands to fill as much of the screen as it can, but isn't actually maximized.  This is not a huge issue, but it's annoying for two reasons:
 - There are gaps at the bottom and sides
 - I can't 'restore' down to a smaller size because the window isn't actually maximized, it's just resized to fill the screen.

Does anyone know why it does this?  Does it do this under GTK environments like GNOME or XFCE?  Is there a workaround?

---

### Post by lykwydchykyn on 2010-03-03
Ok, just to satisfy my curiosity I tried it under openbox and maximize works like normal.

I don't have this problem with other gtk apps, anyone else seeing this?

---

### Post by lykwydchykyn on 2010-03-05
bump.

It appears to be a problem with the gtk version.  When I try the "lucid" version (meaning the lucid toolkit, not the emacs from lucid lynx) it doesn't have this issue.  Of course, it has an issue of using an ugly toolkit, which is not really something I want to live with (plus snapshot is not available with the lucid toolkit).

Anyone?  Even a "yeah, that bugs me as well?"

---

### Post by jpkotta on 2010-03-05
Applications like Emacs or xterm set their window sizes in terms of characters.  See the --geometry option for Emacs (or xterm or just about any other X11 application).  

The point is that these applications don't see sizes in terms of pixels, and any size their windows have is in multiples of "characters" (which is font-dependent).  You will generally not fill your screen perfectly with them when they maximize.  They should still behave as maximized windows though (e.g. unmaximizing returns to the original size).  

You may want to look at the --fullscreen option to Emacs.

---

### Post by lykwydchykyn on 2010-03-05
> **jpkotta said:**
> Applications like Emacs or xterm set their window sizes in terms of characters.  See the --geometry option for Emacs (or xterm or just about any other X11 application).  

The point is that these applications don't see sizes in terms of pixels, and any size their windows have is in multiples of "characters" (which is font-dependent).  You will generally not fill your screen perfectly with them when they maximize.  They should still behave as maximized windows though (e.g. unmaximizing returns to the original size).  

You may want to look at the --fullscreen option to Emacs.

If that's the case, why does it work fine under another WM, or using non-gtk widgets?  Ah well, I don't know.

I guess I could tinker around with geometry on my shortcuts, since I usually want it maximized.  Not sure I want it fullscreen, but that might be a workable compromise.

---

### Post by flippo on 2010-03-05
You can just use vim :-P

(I just couldn't help myself...)

---

### Post by lykwydchykyn on 2010-03-05
> **flippo said:**
> You can just use vim :-P

(I just couldn't help myself...)

Aaaaaaaaaaagh!

[IMG]http://smile.smilies.nl/460.gif[/IMG]

---

### Post by jpkotta on 2010-03-06
> **lykwydchykyn said:**
> If that's the case, why does it work fine under another WM, or using non-gtk widgets?  Ah well, I don't know.

I guess I could tinker around with geometry on my shortcuts, since I usually want it maximized.  Not sure I want it fullscreen, but that might be a workable compromise.

I would play with X resources, because then you won't have to make a distinction between starting it with a short cut and starting it normally.

I just tried running emacs-gtk and emacs-lucid in openbox (running in Xephyr, but that really shouldn't make a difference), and it behaved the same way it always has for me.  Openbox even told me the new geometry while I was resizing, and it was in characters, not pixels.

I have never seen the behavior you have with Emacs, Xterm, or any other similar application.

> **flippo said:**
> You can just use vim

Of course, vim runs in a terminal and gvim behaves the same way as Emacs or any other character-based application, so that really isn't any different.

Edit:  OK, it seems like what openbox is doing is "faking" the edges when maximizing.  The widgets inside the window don't go all the way to the edge, but the window's background is filling in all the extra space at the lower and left edges.  This is happening with GTK or Lucid, or with xterms.  It's a nice effect and I wish my WM did it too.

---

### Post by slygent on 2010-04-23
I came across this many months ago and spent an afternoon trying to work out what was going on. To save time for fellow travellers, the essential problem is described here: [https://bugzilla.novell.com/show_bug.cgi?id=345669](https://bugzilla.novell.com/show_bug.cgi?id=345669)

Basically it is a GTK bug which competes against KWin in deciding the window geometry. Only solution seems to be to use a different toolkit from GTK until it's fixed, unfortunately...

Using the X toolkit here, trying not to look too uncool ;)

---

### Post by metromari on 2011-11-27
Take a look at this:

[http://www.fvwm.org/documentation/faq/#5.16](http://www.fvwm.org/documentation/faq/#5.16)

Some apps like Emacs and xterms might specify resizing increments. The window manager may or may not respect them. Be careful what you ask for: if the window manager ignores the resize increments, you might see little bits of garbage around the edges of your, say, xterm window.

I ran into this when using tiling window managers. Awesome would respect what the apps would say, but then I would get gaps. Xmonad would ignore what the apps say, but then sometimes I would get bits of leftover garbage around the edges of my xterms--I suppose because xterm would not update these parts of the window. Now I use fvwm and just accept the gaps.

kwin might have a way to specify whether or not to respect these suggestions.

---

### Post by xaccrocheur on 2012-05-04
Yeah, that bugs me as well.

---

