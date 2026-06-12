---
title: "xp added by wubi"
date: 2009-11-12
forum: General Help
---

### Post by mrkazoodle on 2009-11-12
Hi

I am running Vista (on an Acer 8935G) and have installed Ubuntu through wubi.
(because I wasn't sure if it would work on my laptop, it didn't and I had to install version 9.04)

It seems that Wubi added some kind of non working windows xp (=useless??). It can be found in the /media folder, but in the /media there isn't a folder for my vista, my vista drive needs to be accessed through the /host folder (no problem there).
But when I open that /host folder I also find folders from the xp installation like 'documents and settings', a folder which was replaced in vista by 'users'.

My question: do I need this 'XP' that takes up 3.7 GB in my media folder and makes it inconvenient to browse my Vista drive?

---

### Post by Mark Phelps on 2009-11-12
Not familiar with the internal structure of a Wubi install, but it certainly does NOT install XP or any other MS Windows OS. 

What it might do is create a file structure that mimics that of XP.

I would be hesitant to remove any directories inside the Wubi install -- as that could very well render it unusable.

---

