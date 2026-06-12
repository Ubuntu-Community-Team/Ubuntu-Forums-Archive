---
title: "glib2.0 problem"
date: 2010-12-22
forum: General Help
---

### Post by keltu77 on 2010-12-22
when compiling anjuta-2.32.0.0  it asks for 'glib-2.0>=2.25.15'  but the ubuntu repos only have glib 2.24.1 . same situatuion with gio-2.0. 
where can i get these packages ? 
I am using ubuntu 10.04  
thanks in advance
ps: I know i can install anjuta from repo but I dont want to.

---

### Post by 3Miro on 2010-12-22
Either look for unofficial PPA providing newer libraries or  upgrade to 10.10 (make sure 10.10 comes with the proper version of gibc).

You can also compile your own version of glibc, but this is an involved process.

---

