---
title: "notifyOSD on wrong monitor (dual monitor)"
date: 2012-05-06
forum: General Help
---

### Post by DavidSommen on 2012-05-06
I run a dual set-up (my 'main' one via VGA, and HDTV via HDMI). Even though this is a minor problem, it is one nevertheless. Every black notification box (internet connection, ejecting usb drives, and so on) appears on my HDMI output. I only use this tv to watch movies and stuff. Is this a bug in compiz/unity? Or has it got to do with wrong settings?

---

### Post by c0mp13371331337 on 2012-05-14
> **DavidSommen said:**
> I run a dual set-up (my 'main' one via VGA, and HDTV via HDMI). Even though this is a minor problem, it is one nevertheless. Every black notification box (internet connection, ejecting usb drives, and so on) appears on my HDMI output. I only use this tv to watch movies and stuff. Is this a bug in compiz/unity? Or has it got to do with wrong settings?
You can start by:
```
sudo apt-get install dconf-tools
```
Then open dconf-editor and navigate to apps > notify-osd.

Change your multihead-mode option to 'focus-follow', and the notifications will appear on whichever monitor the cursor currently resides in.

That's about the extent of any sort of NotifyOSD settings or options, that and gravity.  In previous versions of Ubuntu, there were some forked/patched versions of NotifyOSD that supported an extended feature set, such as precise placement, style, etc.  To the best of my knowledge (and the best of my google-fu) no such thing exists for Precise yet.  There stands the possibility of previous versions working, but I've not tested that.

EDIT: That last sentence ate away at my soul last night and today, so I loaded Ubuntu in a virtual machine and tested.  In all honesty, the old versions are entirely usable.  You need to point to the Lucid repositories for both the patched NotifyOSD, as well as the configuration app:

```
sudo add-apt-repository ppa:amandeepgrewal/notifyosdconfig
sudo add-apt-repository ppa:leolik/leolik
```

At this point, you'll have the Precise repositories, which are non-existent.  You can either manually edit the associated lines in your /etc/apt/sources.list, or go the GUI route and use Synaptic to edit the repos to point to Lucid for both of the above.

Once that's done, refresh your packages with Synaptic, or by using:

```
sudo apt-get update
```

And then use Synaptic to force the leolik version of notify-osd, and also install notifyosdconfig while you're at it.  Once that's done, you've got a fully-functional, fully configurable NotifyOSD.

However, there are some slight caveats: theme and corners.  The theme doesn't match the new Precise NotifyOSD theme, it gets reverted back to the dark-gray color.  That's an easy fix though, as NotifyOSDConfiguration provides options for theming.

Then there are the corners.  For some reason (at least in my testing), only the top-left corner of each NotifyOSD bubble was rounded, the other three corners were squared, which looked a bit ugly.  Assuming you don't know how to fix it in the code, which I certainly don't, you can either live with it, or just set Corner Radius to 0px and make ALL corners square.

---

