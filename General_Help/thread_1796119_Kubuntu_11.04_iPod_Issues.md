---
title: "Kubuntu 11.04 iPod Issues"
date: 2011-07-03
forum: General Help
---

### Post by lakerssuperman on 2011-07-03
I recently switched to running the latest Kubuntu as I was having too many problems with Unity.  One issue I have run into is using Amarok and for that matter KDE with my two iPods.  My 120gb classic gets recognized by the system but Amarok will not load the collection information, instead reporting that it has zero songs.  The iPod Touch 3rd generation is only recognized as a camera by the system and doesn't show up at all in Amarok.  I know for a fact that the Classic works with Ubuntu 11.04 and I have not yet tried the Touch on anything but Ubuntu 10.10 which it has no problem with.The Classic also had no issues with Kubuntu 10.10 when I had that installed. 

Does anyone have similar issues?  Has anyone figured out how to fix it.  I find it odd that it works with Ubuntu 11.04 and not Kubuntu 11.04.  To me that seems to be a KDE issue.  I am running KDE 4.6.4 from the Kubuntu Desktop PPA.

Thanks for any help you can offer.

---

### Post by wolfen69 on 2011-07-03
Try **gtkpod** for transferring music. You may also need the **ifuse** package.

---

### Post by lakerssuperman on 2011-07-03
Thanks for the quick answer.  I should add, GTKPod works with my Classic.  It doesn't work with the Touch on Kubuntu 11.04.

However, I am evaluating Kubuntu 11.04 for a friend and I wouldn't want to try to have them mess with GTKpod.  I want them to use a jukebox program for both listening and transferring music.  They have an iPod and this would be a big issue to work around.

---

### Post by lakerssuperman on 2011-07-03
UPDATE: I left my classic plugged in and it just randomly loaded the collection.  However, it took a good amount of time and Amarok won't transfer songs to the iPod.

---

### Post by lakerssuperman on 2011-07-04
I manually upgraded to the latest libimobile library, version 1.1.1.  This solved my iPod issues.

---

