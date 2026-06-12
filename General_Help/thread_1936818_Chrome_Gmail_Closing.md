---
title: "Chrome Gmail Closing"
date: 2012-03-06
forum: General Help
---

### Post by Auroleus Bombastus on 2012-03-06
Hello.  (Hi.)  

I'm trying to create a gmail account and whenever I get to the enter info page Chrome unexpectedly closes and it does the same thing on Chromium.  Running 11.10 . . . can somebody please fill me in as to what is happening with my browser?  Thank you for your kind attention.

---

### Post by sanderd17 on 2012-03-06
Can you launch chromium from the terminal?

```

chromium

```

Normally, it will give you some output when it crashes, if you share that output with us, we can analyse it.

---

### Post by Auroleus Bombastus on 2012-03-06
Strange...  When I opened Chromium through the terminal it let me create an account.  No idea as to why it let me do this...  Do these codes mean anything to you? 

```
(chromium-browser:2276): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2276): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2276): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(chromium-browser:2276): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(exe:2356): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(exe:2356): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(exe:2356): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(exe:2356): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
[2276:2276:5474506894:ERROR:browser_main_loop.cc(128)] Gtk: gtk_widget_size_allocate(): attempt to allocate widget with width -2147483648 and height 965
[2276:2276:5579369692:ERROR:browser_main_loop.cc(128)] Gtk: gtk_widget_size_allocate(): attempt to allocate widget with width -2147483648 and height 965
pocomas27@Gertrude:~$
```

---

### Post by Auroleus Bombastus on 2012-03-06
> **sanderd17 said:**
> Can you launch chromium from the terminal?

```

chromium

```

Normally, it will give you some output when it crashes, if you share that output with us, we can analyse it.

Okay, so it may have worked once, but I reset my box and now it's doing it again... allow me to share with you the code you're probably looking for.

```
chromium-browser: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted

```

---

### Post by sanderd17 on 2012-03-08
> **Auroleus Bombastus said:**
> Okay, so it may have worked once, but I reset my box and now it's doing it again... allow me to share with you the code you're probably looking for.

```
chromium-browser: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted

```

I've googled it, I've encountered people with the same problems, but I haven't found a solution.

You will need to search people with a better knowledge of chrome.

Try google groups such as this: [http://www.google.com/support/forum/p/Chrome/thread?tid=5a8e6bdbed65a184&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=5a8e6bdbed65a184&hl=en)

---

### Post by Auroleus Bombastus on 2012-03-14
Thanks for the redirect.  There's another piece of information (problem) that occurs but I'm not sure that it's related.  When I installed 11.10 I had a hell of a time getting my monitor and the OS to get along... had to rewrite the xorg.conf.  And to this day, when I boot up my box it throws up a white screen with black lines...  half the time it gets stuck on a screen like this and won't boot so I have to cold reset.  Seems to be happening more frequently nowadays.  I was wondering if you have any knowledge of this problem?  If so, is it harmful to my box?  Thanks again.

---

### Post by sanderd17 on 2012-03-15
> **Auroleus Bombastus said:**
> Thanks for the redirect.  There's another piece of information (problem) that occurs but I'm not sure that it's related.  When I installed 11.10 I had a hell of a time getting my monitor and the OS to get along... had to rewrite the xorg.conf.  And to this day, when I boot up my box it throws up a white screen with black lines...  half the time it gets stuck on a screen like this and won't boot so I have to cold reset.  Seems to be happening more frequently nowadays.  I was wondering if you have any knowledge of this problem?  If so, is it harmful to my box?  Thanks again.

No software problem is harmful for your box, with the only exception being your battery which can be effected by bad power management (but a battery only lasts for about 3 years anyway).

Now, for your problem, can you edit your boot flags.

You do not need to add boot flags, only delete the "quiet splash" flags. You can see how to alter boot flags in my signature.

By deleting this flags, Ubuntu will show messages during the boot. That way, you can see where it hangs, and we might be possible to see what's wrong.

---

