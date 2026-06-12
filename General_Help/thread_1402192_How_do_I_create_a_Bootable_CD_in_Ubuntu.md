---
title: "How do I create a Bootable CD in Ubuntu?"
date: 2010-02-08
forum: General Help
---

### Post by Rytron on 2010-02-08
I came across this [tutorial]("http://www.youtube.com/watch?v=AVZMvGZjOWA"). It is for Windows however. What program would be the equivalent to ImgBurn?

---

### Post by jamesisin on 2010-02-08
If you are running Ubuntu, you can navigate to System --> Administration --> Create a USB startup disc.

If you want to download the image files from the site in the tutorial, you can use them too.  You will want to change the file extension from .img to .iso at which point you can simply right-click on an ISO and choose "Write to Disc...".

---

### Post by Rytron on 2010-02-09
Thank you very much jamesisin.
:popcorn:

---

### Post by warfacegod on 2010-02-09
Remastersys might be worth looking into as well as jamesisins' post.

---

### Post by Rytron on 2010-02-09
Cheers warfacegod. ;)

---

### Post by Rytron on 2010-02-09
> **jamesisin said:**
> If you are running Ubuntu, you can navigate to System --> Administration --> Create a USB startup disc.

If you want to download the image files from the site in the tutorial, you can use them too.  You will want to change the file extension from .img to .iso at which point you can simply right-click on an ISO and choose "Write to Disc...".

I cannot go any further. I guess .img is not accepted. I renamed it to .iso but no luck. Do I need to convert the .img file to .iso?

Edit: ImgBurn works fine in Wine!

---

### Post by warp99 on 2010-02-09
Here's a help guide on burning an .img file in Ubuntu:

[https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu](https://help.ubuntu.com/community/Installation/FromImgFiles#Ubuntu)

The usb image writer utility is available in the repositories so you can install that through Synaptic or in the Ubuntu Software Center.

---

### Post by Rytron on 2010-02-09
Hi warp99. I appreciate it. :)

---

### Post by jamesisin on 2010-02-09
You can't combine my two suggestions; they are meant to be separate.

The Ubuntu installer discs can be used as Live CD's themselves.  You can also create one of the Ubuntu Live discs as a bootable USB drive using my first suggestion.

If you want to create a bootable CD using one of those images (.img) from that site, simply change the extension to ISO (.iso) and right-click to choose "Write to disc...".

(Or rather, if there is a way to combine them I don't know it.)

---

### Post by Rytron on 2010-02-09
Thanks again jamesisin.

---

### Post by jamesisin on 2010-02-09
Of course.  If that works out for you, remember to mark the thread as SOLVED in Thread Tools above.

---

