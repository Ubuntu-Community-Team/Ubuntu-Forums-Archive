---
title: "Filesystem syntax help needed"
date: 2009-12-09
forum: General Help
---

### Post by Linc_mc on 2009-12-09
I am trying to run world of warcraft on ubuntu 9.10 using wine and found that i can run it using the the one thats already installed on my windozer partition. However I am having trouble figuring out the syntax to tell wine where to look for it as I have ubuntu installed on a completely different hard drive. I have tried these instructions but just can't seem to get it.


In a system with Fuse, such as Ubuntu or Fedora, a default install of wine will run WoW from a mounted drive that has World of Warcraft installed just by adding the -opengl flag at the end: 

 wine "/media/windowsdrive/WorldofWarcraft/Wow.exe" -opengl

where "windowsdrive" is the name of the drive in /media that you have mounted. Replace the path name with your install! You could have installed it in Program Files or a different folder. Something to note; if you run WoW in Windows after running it in linux, you will have to change a few video settings back, like the shadow quality.

---

### Post by audiomick on 2009-12-09
Linc_mc, what is it that you don't get?
The instructions you have presumably quoted, and using "quote" markers would not hurt;), seem pretty clear.

---

### Post by Linc_mc on 2009-12-09
thanks but i got it

---

