---
title: "How to remove iso images from virtual media manager"
date: 2010-12-26
forum: General Help
---

### Post by karthick87 on 2010-12-26
I had a DVD image attached to Virtualbox via Virtual  Media Manager and had it deleted from my harddrive without removing or  "releasing" it from Virtual Media Manager.
  Now the image is still shown in Virtual Media Manager but the remove and release options are greyed out.Is there a way to get rid of the image shown in Virtual Media Manager?  
[IMG]http://imgur.com/JLWAf.png[/IMG]

---

### Post by Vigh on 2010-12-26
Re-rip the DVD-image, place it in the exact same location it was originally loaded from, load the virtual HDD, unmount it from the Virtualization, then turn off the virtual HDD and remove from the list, and then delete the DVD-image file

otherwise your probably looking at a virtualbox purge and reinstall
which is not a major issue provide you back-up the *.vdi virtual hdd file

*.vdi are not hard to restore

---

### Post by karthick87 on 2010-12-26
No other way to remove??

---

