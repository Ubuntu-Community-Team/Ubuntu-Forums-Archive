---
title: "How can I use my pre-downloaded iso for Wubi?"
date: 2010-09-16
forum: General Help
---

### Post by dolphin194 on 2010-09-16
Ok, so here's the deal. I have downloaded the Ubuntu Netbook 10.04 iso about a week ago, and it's in the same folder as Wubi. It keeps trying to download another image even though the one is in the same folder. The image is not corrupted. How can I use the pre-downloaded iso?

---

### Post by andrewthomas on 2010-09-16
You can't 

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)

---

### Post by dolphin194 on 2010-09-16
> **andrewthomas said:**
> You can't 

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)
But why does it say on [http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) that I can

             **Can I use an existing ISO/CD instead of letting Wubi download a new one?**

             Yes, physical CDs will be detected automatically,  pre-downloaded ISOs should be placed in the same folder as Wubi.exe.  Please note tha Wubi 8.10 requires the Desktop 8.10 CD/ISO. The DVD and  Altrenate CD/ISO will not work. You can find the 8.10 ISO [here]("http://releases.ubuntu.com/8.10/").  If Wubi does not find an appropriate ISO/CD and/or if the ISO/CD is  corrupted, it will automatically download a new ISO. It is recommended  to let Wubi download the ISO for you.

---

### Post by jshepherd on 2010-09-16
You should just be able to make a live dvd and when you load the disk windows will detect the Wubi part.

---

### Post by dolphin194 on 2010-09-16
> **jshepherd said:**
> You should just be able to make a live dvd and when you load the disk windows will detect the Wubi part.
Could I mount the image with **SlySoft Virtual CloneDrive?**

---

### Post by bcbc on 2010-09-16
The prob is that wubi.exe is on version 10.04.1 and the netbook edition wasn't included in that release. So wubi.exe will keep trying to download the netbook edition and keep failing.

You need the 10.04 wubi.exe and you can find it here: [http://people.canonical.com/~evand/wubi/lucid/](http://people.canonical.com/~evand/wubi/lucid/)
It's rev189

---

