---
title: "Not able to Mount CD-Rom"
date: 2010-06-26
forum: General Help
---

### Post by mparker1113 on 2010-06-26
Hi, 

I have loaded Ubuntu server 10, I need to access files on my cd-rom drive and am not having success. I don't see hdc or anything like that under /dev. When i ran wodim -- devices, i get "Cannot open SCSI Driver !" , etc... which i read means that i am not part of the cdrom group. I couldn't find a cdrom group, so i created one, and then added myself to it. 

I still get teh same error message when running wodim --devices.

Any help would be much appreciated.

Mike

---

### Post by mparker1113 on 2010-06-27
So, I was able to get the files that i needed by using the GUI and under the PlacesMenu,choosing "Computer".  But, i still am not sure how i can access the cd from the command line..

---

### Post by Chame_Wizard on 2010-06-27
You don't need do use the command line to access your cd,Nautilus can open it for you.

Just tested out a with audio disc for Japanese learning,Dolphin is accessed it fine.:lolflag:

---

