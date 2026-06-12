---
title: "Recording 3D cube is horrible"
date: 2009-08-11
forum: General Help
---

### Post by Cfhs_1 on 2009-08-11
I'm using ubuntu on my system. It has 2.5GB RAM, A 2.8GHz P4, with a Nvidia GeForce 5200 with 128 MB RAM. When I try to record my cube with GTK RecordMyDesktop, It comes out all garbled and trashy. you can see a video here:

[http://www.youtube.com/watch?v=uMSwAzZlWbg](http://www.youtube.com/watch?v=uMSwAzZlWbg)

any help would be great!

---

### Post by MickS on 2009-08-11
I have the same problem, can't help I'm afraid other than to give your post a bump.

Mick

---

### Post by scouser73 on 2009-08-11
You could try [[COLOR="Red"]**Screen Toaster**[/COLOR]]("http://www.screentoaster.com/") and see if that is any better for your needs.

---

### Post by 3rdalbum on 2009-08-11
Try running "recordmydesktop" on the command line. My guess is that the GTK frontend is disabling the "full shots" option even when Compiz is running, which is known to cause garbled output. If you run recordmydesktop from the command-line, it will automatically turn on "full shots" when it detects Compiz.

---

### Post by Cfhs_1 on 2009-08-11
> **3rdalbum said:**
> Try running "recordmydesktop" on the command line. My guess is that the GTK frontend is disabling the "full shots" option even when Compiz is running, which is known to cause garbled output. If you run recordmydesktop from the command-line, it will automatically turn on "full shots" when it detects Compiz.


Tried that. It just gives me the same results. could it have somthing to do with my hardware being to old?

---

### Post by Cfhs_1 on 2009-08-11
> **scouser73 said:**
> You could try [[COLOR="Red"]**Screen Toaster**[/COLOR]]("http://www.screentoaster.com/") and see if that is any better for your needs.

Screentoaster seems like it would be perfect, but for some reason
when I record it just captures mouse movement and anything else I do ( bring up windows, click on menus, use compiz) just doesn't show up at all....

---

