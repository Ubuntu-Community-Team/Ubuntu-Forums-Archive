---
title: "Google earth ( | ) for all the font characters"
date: 2011-03-24
forum: General Help
---

### Post by kmsalex on 2011-03-24
I was having this problem with 4.x something for a while so I checked online for an update (the build in one said it was up to date) and downloaded/installed 6. wouldn't run, finally got it to run after installing some package or another, finally it lunched! (this was like an hour latter) then to my horer i saw the same problem.

bellow I've included a picture to show you what i mean. The program still runs fine but the tools like the ruler are useless and the search box is unread able (though it still works). 

Any advice would be greatly appreciated, I've run out of ideas.

---

### Post by Meizirkki on 2011-03-26
I installed the Google Earth 6 today as well, from the .deb provided by google. I too, had to install lsb-core to get it to start.

I have the same problem with characters, except they are squares instead of |

Running Ubuntu 10.04 32bit

---

### Post by eracho on 2011-04-30
I have the same problem, running Ubuntu 10.04 64bit.

---

### Post by Vaphell on 2011-04-30
try to uninstall and then reinstall msttcorefonts package.

---

### Post by kmsalex on 2011-04-30
> **Vaphell said:**
> try to uninstall and then reinstall msttcorefonts package.

Yes that worded :D thank you so much, I had convinced myself I would have to wait till i upgraded to 12.04 for Google earth to work again.

Thank you very mutch again sir :KS

---

### Post by eracho on 2011-05-02
it work for me too, 
[FONT=Verdana]$ sudo apt-get remove msttcorefonts
[/FONT]$ sudo apt-get install msttcorefonts
thanks!!

---

