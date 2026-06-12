---
title: "Firefox not displaying content properly"
date: 2009-08-02
forum: General Help
---

### Post by Rikki123s on 2009-08-02
Hey everyone!

For some reason my netbooks version of Firefox has recently stopped showing most of the content within every web page that it visits. Here is a screen shot:

[IMG]http://img.photobucket.com/albums/v606/Rikki123s/Screenshot-1.png[/IMG]

As you can see, all interactivity is still in place, and most of the images, but for some reason the style and background colour is not displaying and in some instances, missing images. I have tried both firefox 3.0 and shiretoko (firefox 3.5)

Please can anybody help?

Rik...

---

### Post by pytheas22 on 2009-08-02
Try refreshing your Firefox configuration with this command:
```

mv ~/.mozilla ~/.mozilla-OLD
```

Then restart Firefox.  Does this work better?

Note that this will cause you to lose any extensions, passwords, etc. that you have saved in Firefox, but it may be possible to recover them later if this is a big deal to you.

---

### Post by Rikki123s on 2009-08-03
That actually worked, thank you pytheas. I take it that would change the name of the Firefox settings file, making it unreadable to Firefox and thus creating a new one for itself?

Once again, thanks.

[IMG]http://img.photobucket.com/albums/v606/Rikki123s/Screenshot-1-1.png[/IMG]

---

### Post by think13 on 2009-08-03
> **Rikki123s said:**
> I take it that would change the name of the Firefox settings file, making it unreadable to Firefox and thus creating a new one for itself?

Exactly right (well, it's technically a folder, not a file, but close enough).  If you have settings you wish to recover from your old setup, ~/.mozilla would be the first place to look.

---

