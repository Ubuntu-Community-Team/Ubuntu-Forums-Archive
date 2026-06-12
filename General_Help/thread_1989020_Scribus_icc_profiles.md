---
title: "Scribus icc profiles"
date: 2012-05-28
forum: General Help
---

### Post by cscj01 on 2012-05-28
I have Ubuntu 11.10 and Scribus 1.4.1.  In Scribus, if I try to change the path for icc profiles to ~/.local/share/icc, that option is grayed out.  I checked that the required software associated with littleCMS and icc-profiles were installed and found something I am not sure of what the effect might be.  It seems I have liblcms2-2 (2.2+git20110628-2ubuntu2) and liblcms1 (1.19.dfsg-1ubuntu2) both installed.  Under dependencies, they both break any packages installed that are not equal to their versions within their respective trees.  That is liblcms2-2 breaks any other liblcms2-2 not equal to the installed release, and liblcms1 breaks any other liblcms1 not equal to the installed release.  However, they say nothing about co-existing or any problems of liblcms2-2 breaking any liblcms 1 or vice versa.

Does anyone know if having both versions installed is a problem?  Could there be some other icc aware applications that need liblcms1 but not liblcms2-2?  Thanks for any help.

---

### Post by cscj01 on 2012-05-28
I suppose if I search more places, I could avoid asking these questions in the first place.  Oh well.

It seems that one can only change the paths for the icc profiles with no documents open.

Hope this helps someone other than me.

---

