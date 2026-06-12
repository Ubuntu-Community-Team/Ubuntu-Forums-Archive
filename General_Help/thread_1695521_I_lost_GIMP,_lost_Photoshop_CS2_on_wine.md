---
title: "I lost GIMP, lost Photoshop CS2 on wine"
date: 2011-02-26
forum: General Help
---

### Post by joecichocki on 2011-02-26
I am running Ubuntu 9.10 and have been doing so for about 1.5 years. I do not know any commands other than what I might find on the internet, so you know that I am at best an automatic update guy. If an application doesn't install itself, well, I don't use it.

 I had been using my GIMP via Bibble 5 Linux without any problems whatsoever. I even downloaded wine and was able to install Photoshop CS2 and use it no problems, for several months. GIMP stopped appearing first. I have no reason to believe so, but I suspect something which came with one of my automatic updates affected it. No way, nohow will GIMP start. I have tried uninstalling it and reinstalling it several times, and nothing happens. Now today I tried to open CS2 as I have many times before, and nothing happens. No messages, no nothing. Just a spinning little ball of a cursor which turns into the arrow after about a minute.

Does anyone have any idea what I can do. I really love using GIMP and my CS2, so this is kind of compromising my sanity.

I have a Compaq Presario R3100 with an AMD 1.6GHz processor and 2 GHz Ram.

I would appreciate any help I can get!!

Thank you all!

Joe Cichocki

---

### Post by Old *ix Geek on 2011-02-26
Try renaming your GIMP directory to something else, then try firing up the GIMP and see if it works. Something may have gotten corrupted in its directory. I'm using version 2.6 and in my home directory I have this subdirectory, **.gimp-2.6**

Yours may have a slightly different name if it's not the same version.

Just **mv** it to something else, like **.gimp-2.6_old**, to see if that solves the problem. If it does, you're going to lose all your settings and things you've tweaked in the GIMP, but at least it'll work again! Of course, then you can always copy files back over from **.gimp-2.6_old** to the newly-recreated **.gimp-2.6** and see at what point it fails.

I can't really help you with your other issue, unless it's something similar to the above.

---

### Post by cchhrriiss121212 on 2011-02-26
Open the terminal and type gimp, then post the output you get.

---

