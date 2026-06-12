---
title: "Emacs 23 fonts are HUGE!"
date: 2010-02-05
forum: General Help
---

### Post by Timtro on 2010-02-05
Hi,

I'm running UNR on my little twerp. I actually quite like the interface aside from a few irritating points, and one big one. When I start up emacs 23, the document font is HUGE. The tooltip fonts are HUGE too.

I don't know much about emacs bing a Vim user, but I'm trying to learn. I tried the solutions offered here:
[http://stackoverflow.com/questions/1516847/emacs-23-and-font-size](http://stackoverflow.com/questions/1516847/emacs-23-and-font-size)
but neither of the snippets (placed in my .emacs file) nor running emacs as a server seemed to work.

As a final note, I'm running a pretty default install, but I did turn off the automatic maximization, which was getting on my nerves:

```
gconftool-2 --set /apps/maximus/no_maximize --type BOOL true
```

---

### Post by jpkotta on 2010-02-06
First off, this is not something that Emacs handles very well IMO, but you can get it to do whatever you want.

What I do is set my default face to be what I want in customize (M-x customize-face RET default RET), then I have some X resources to set Emacs initial frame[1] size.  I set the font height in .Xresources too because I share my config files across machines and the netbook needs a different height. 

```

Emacs.Fullscreen: maximized
! default font height
Emacs.default.attributeHeight: 92

```

The advantage of setting these things in .Xresources is that they're applied very early in Emacs's initialization, whereas if you add them to your .emacs file they will be applied very late.  This reduces all of the weird resizing at start up (running in daemon mode also helps to mitigate this).  You will want to run the following command after you log in (and how that is done depends on what window manager you use) to apply the ~/.Xresources:

```

xrdb -merge ~/.Xresources

```

[1] In case you haven't figured it out already, when Emacs talks about windows, it's talking about the area that the buffer is displayed in.  What everyone else calls windows, it calls frames.  And of course this terminology is completely opposite of the same terms in web browsers.

---

### Post by Timtro on 2010-02-08
Thanks jpkotta, I'll try that out as soon as I get home. Either way, since I know next to nothing about emacs, your post was still very elucidating.

---

### Post by nullie on 2010-03-11
I've found out this is due to DPI settings.

GTK apps use DPI settings from Appearance Preferences - Font Rendering Details, which is set by default to 96 dpi, so all gtk apps look ok.

But Emacs uses X server dpi settings which on netbooks is often about 130 dpi due to high resolution and small display size.

I've not found a non-hackish way to pass -dpi 96 argument to X server, so I took advantage of nvidia driver and set dpi with Option    "DPI"  "96 x 96" in xorg.conf

For other videocards should be also possible to fix this by specifying correct DisplaySize option in xorg.conf

For now, Emacs fonts have same size as rest of my environment.

---

### Post by Timtro on 2010-05-17
> **nullie said:**
> I've found out this is due to DPI settings.

GTK apps use DPI settings from Appearance Preferences - Font Rendering Details, which is set by default to 96 dpi, so all gtk apps look ok.

But Emacs uses X server dpi settings which on netbooks is often about 130 dpi due to high resolution and small display size.

I've not found a non-hackish way to pass -dpi 96 argument to X server, so I took advantage of nvidia driver and set dpi with Option    "DPI"  "96 x 96" in xorg.conf

For other videocards should be also possible to fix this by specifying correct DisplaySize option in xorg.conf

For now, Emacs fonts have same size as rest of my environment.

Thanks for the find. I never did get around to fixing this before I decided that perhaps if I need emacs on UNR, I might just as well have the full desktop. I don't find UNR all that light compared to the full gnome desktop. If I'm going for lite, I much prefer crunchbang (#!), despite the fact that it doesn't actually attempt to be a light weight desktop.

---

