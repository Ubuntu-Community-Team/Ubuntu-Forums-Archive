---
title: "Bibus not working in 12.04"
date: 2012-04-28
forum: General Help
---

### Post by Biomante on 2012-04-28
Hi there

I upgraded to precise yesterday and now I can't make Bibus to work properly (it is kind of an emergency, this software is essential for my job). When I try to insert a reference I get the next message:

Cannot connect to Openoffice. See Documentation.
Cannot connect to Openoffice. See Documentation.
Connector : couldn't connect to pipe OOo_pipe(10))

I tried lowering the Macros security level in Libreoffice to Medium, and adding a macros trusted route (/usr/share/bibus), but it didn't work.

Any ideas? Thanks in advance.

---

### Post by Biomante on 2012-04-28
Bump

---

### Post by Biomante on 2012-04-28
No ideas? anyone?

---

### Post by kouakou on 2012-04-30
I have the same problem. I was lucky enough to do a clean install of 12.04 on one of my laptops and that works fine. Even works better than when I used bibus on 11.04. for the other one, I cannot connect after I upgraded. I am guessing it is a problem with the upgrade. I may just have to scrap and do a clean install... unless someone has a solution

---

### Post by Dimpflmoser on 2012-05-01
I have the same problem. I tried deinstaling bibus, but even with newly installed bibus it was the same. :( 
Are we the only ones with this problem?!?

---

### Post by vanadium on 2012-05-02
Rerun the first connection wizard. Reboot the system and then check wether bibus can talk to libreoffice.
For me, it works, but I am having trouble with the finalize function.

---

### Post by kouakou on 2012-05-03
Vanadium, To fix the finalize problem, remove bibus or better yet dont use the one provided by the repository. I downloaded the one from sourceforge. when installed do: 
sudo nano /usr/share/bibus/bibOOo/bibOOoBase.py

search for line 748 and change 
**"private:stream"** to **self.model.getLocation()**

hope that helps

---

### Post by vanadium on 2012-05-07
kouakou, thank you very much! I installed version 1.5.2 from soundforge, and "finalize" worked out of the box. I will keep your suggested patch indeed in case I would encounter issues later. I am working with Ubuntu 12.04.

---

