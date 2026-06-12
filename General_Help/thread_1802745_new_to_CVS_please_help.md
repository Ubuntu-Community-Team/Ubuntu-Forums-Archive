---
title: "new to CVS please help"
date: 2011-07-12
forum: General Help
---

### Post by conradin on 2011-07-12
hi all, 
Im trying to update drupal 7-beta to drupal 7-4 using CVS
I want to view the Repo directory to find the package name or find the package name in some other way. the code I used previously to update my Drupal install was:```
cvs -z6 -d:pserver:anonymous:anonymous@cvs.drupal.org:/cvs/drupal co -r DRUPAL-7-4-BETA2 -P -d www/ drupal

```

yes, I am reading the man page,

---

### Post by conradin on 2011-07-13
Ok, I couldnt figure it out, So I dumped everything in ths www folder, extracted the 7.4 drupal download to /var/www and that seems to have worked. Thats not the cvs solution, and drupal seems to be using GIT. Not sure if the two are interchangeable. But my problem is solved!

---

