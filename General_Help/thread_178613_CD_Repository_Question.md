---
title: "CD Repository Question"
date: 2006-05-18
forum: General Help
---

### Post by DirtDawg on 2006-05-18
My Linux box has never seen the internet. I read that the install CD could be used as a [basic] repository, but lost my install cd awhile ago. I'm using Hoary.

Question: Since I've never updated my version of Hoary, if I download and burn a new .iso image and attempt to use it as a repository, is there a chance installing new applicatyions could "break" my os? 

I'm worried newer packages could need or install newer dependancies and wonder if this could be a potential problem.

Thank you

---

### Post by Sef on 2006-05-18
> Question: Since I've never updated my version of Hoary, if I download and burn a new .iso image and attempt to use it as a repository, is there a chance installing new applicatyions could "break" my os?

Yes.  If you download and burn an new iso, do a clean install.  If you try to install the repositories, your system will break.

---

### Post by az on 2006-05-18
[QUOTE=DirtDawg]if I download and burn a new .iso image and attempt to use it as a repository, is there a chance installing new applicatyions could "break" my os? 

I'm worried newer packages could need or install newer dependancies and wonder if this could be a potential problem.
[/QUOTE]
The package manager will resolve those dependencies and refuse to install the packages with the missing dependencies.

If you add the cd and then ask it to upgrade and it wants to remove essential packages, you'll know why.  But if you pretty much only have stuff from main, it will work fine.

---

### Post by DirtDawg on 2006-05-18
Great! Thanks guys.

---

