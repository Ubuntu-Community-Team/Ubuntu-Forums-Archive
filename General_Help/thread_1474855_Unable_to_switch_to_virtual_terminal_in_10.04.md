---
title: "Unable to switch to virtual terminal in 10.04"
date: 2010-05-06
forum: General Help
---

### Post by purecharger on 2010-05-06
I've upgraded from 9.10 to 10.04 and now I am unable to switch to a virtual terminal (ctrl-alt-{f1 to f6}). The screen switches, I get a black screen with some green scan lines at the top and nothing else. I am then unable to switch back to X (ctrl-alt-f7), forcing me to reboot via ctrl-alt-del.

Any ideas why this would happen?

Thanks!

---

### Post by longanduselessname on 2010-05-06
Maybe a graphics problem, are you using restricted video card drivers?

---

### Post by purecharger on 2010-05-06
> **longanduselessname said:**
> Maybe a graphics problem, are you using restricted video card drivers?

Yes, I am using the nVidia driver for my Quadro card. I'm trying to drop to the terminal to upgrade the driver..

---

### Post by purecharger on 2010-05-06
After more research I've tried adding UseVBios=0 to the nvidia module configuration, and still no luck...

---

### Post by longanduselessname on 2010-05-06
> **purecharger said:**
> After more research I've tried adding UseVBios=0 to the nvidia module configuration, and still no luck...

[http://ubuntuforums.org/showpost.php?p=9249264&postcount=5](http://ubuntuforums.org/showpost.php?p=9249264&postcount=5)

It was that post in another thread that reminded me of your problem. I am guessing that, since you have a Quadro card, that you are not on a laptop. 

I suggest you post your hardware specs, maybe take a photo of the messed up terminal screen with a camera. 

Besides that I don't really have any ideas.

---

