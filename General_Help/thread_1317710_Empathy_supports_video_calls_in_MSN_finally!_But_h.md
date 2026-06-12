---
title: "Empathy supports video calls in MSN finally! But how does it work?"
date: 2009-11-07
forum: General Help
---

### Post by s3a on 2009-11-07
(Ubuntu 9.10) I right clicked on a bunch of my contacts' names and none of them have the "Make video call" or whatever it is exactly in dark letters (active), instead it's light gray (inactive) letters.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by antalas on 2009-11-12
hy s3a, i had the same problem: 
:P these are the instructions (from empathy official FAQ):

Ubuntu disabled audio/video support in telepathy-butterfly (the MSN backend) because this new feature got introduced too late and that feature didn't get much testing. 
You can get more up to date packages from our telepathy ppa, they have audio/video enabled for MSN:

-add the sources:

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

-and then:

sudo apt-get update[COLOR=Black]
[/COLOR]sudo apt-get upgrade

;) that's all

---

### Post by whirl on 2009-12-08
> **antalas said:**
> hy s3a, i had the same problem: 
:P these are the instructions (from empathy official FAQ):

Ubuntu disabled audio/video support in telepathy-butterfly (the MSN backend) because this new feature got introduced too late and that feature didn't get much testing. 
You can get more up to date packages from our telepathy ppa, they have audio/video enabled for MSN:

-add the sources:

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

-and then:

sudo apt-get update[COLOR=Black]
[/COLOR]sudo apt-get upgrade

;) that's all

Sounds good but once I upgraded it removed my empathy all together (shouldve read it more thoroughly I guess) and I had to install it again. Once I did it, empathy doesnt "go hide" in to the IM indicator applet anymore. Any ideas?

Cheers!

---

### Post by zaheer116 on 2009-12-16
I have the same problem, any solution?

---

### Post by henriquemaia on 2009-12-21
I think you have to install the empathy-megafone-applet package that you find on synaptic. That will do the trick (I think).

---

