---
title: "KDE reads and installs fonts from disk even though I do NOT want them installed"
date: 2011-05-06
forum: General Help
---

### Post by Abdus on 2011-05-06
Ubuntu 10.10, up to date KDE.

I got quite a collection of fonts on one of my disks. I noticed that my KDE reads the folder the fonts are stored in and installs them all, even though I don't think I ever pointed it to that folder, and certainly I never instructed KDE to install them. They trash my applications. [-(

I started font installer and "switched off" the fonts in question, only to notice that KDE moved them somewhere else, from the folder I store them. [-X

I don't want them installed automagically, I don't want them moved from my folder. I want KDE to get the hell out of my private disk and let me decide what to install and when. How to do that? Is there some hidden config? :-k

Thanks for any help.

---

### Post by Abdus on 2011-05-06
Solved.

I edited file
/home/abd/.config/font-manager/directories.conf
and eleted the line that was pointing to the folder with fonts in question. Font-manager stopped seeing the folder, no more trouble. :D

---

