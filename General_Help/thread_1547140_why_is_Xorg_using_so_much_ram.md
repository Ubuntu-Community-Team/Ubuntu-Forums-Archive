---
title: "why is Xorg using so much ram?"
date: 2010-08-06
forum: General Help
---

### Post by blur xc on 2010-08-06
I currently have one user logged in, and no applications open.  My system is using 1.8G of ram, and my conky is showing that Xorg is using 22.92% of it...

On a fresh boot, with one user logged in, it normally uses about 500 - 600mb...

Any clues to what this is, and how to free up that ram?  I was using Google Earth a minute ago (it's closed now), could that have something to do with it?

Thanks,
BM

---

### Post by dino99 on 2010-08-06
yes google earth need a bunch of ram

check that your installation is not missing some packages:

sudo apt-get update
sudo apt-get install -f

---

### Post by snowpine on 2010-08-06
Sounds normal to me; this is why Ubuntu recommends 1gb minimum RAM. As long as your system is functioning normally, there is no reason to worry about RAM usage until it hits 100%. :)

---

### Post by blur xc on 2010-08-06
Why is the ram not released after google earth is closed?  Is it saving it in cache until I need some other software to use it?

I only have 4gigs, and I get close to using it up often.  I desperately need more ram for what I do.  So, when I've got almost 2gigs used up when nothing is running, it worries me for when I try to run a program that is also ram hungry...

Thanks,
BM

---

### Post by snowpine on 2010-08-06
You might find this informative: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

