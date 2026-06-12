---
title: "back up downloaded files"
date: 2010-05-22
forum: General Help
---

### Post by alenn on 2010-05-22
how to back up programs which I have downloaded from ubuntu softvare center. I want to upgrade from 9.10 to 10.04 but I don't want to download everthing after I upgrade.
I want to make clean install of OS.

---

### Post by wojox on 2010-05-22
Have a look at this [Package installation after re/new install (Ubuntu)]("http://stringofthoughts.wordpress.com/2009/04/29/package-installation-after-renew-install-ubuntu/") 

Maybe what your looking for.

---

### Post by jamesisin on 2010-05-22
It's not clear from your post, but if you run the upgrade you shouldn't have to reinstall software.  If you do a clean install by wiping your previous install then you will have to reinstall various applications.

The solution wojox links to will help in the case of a clean installation; however, applications which have been removed from the standard repositories will need help (and you will have to add in any special repositories you had added previously--unless Canonical has newly included those applications in the standard repos).

---

### Post by alenn on 2010-05-22
ok, I think that wojox solution will help me, but can I find that folder in which are stored those packages so I can just copy them to some other storage hardvare without having to download them again.

---

### Post by alenn on 2010-05-22
?????

---

### Post by wojox on 2010-05-22
> **alenn said:**
> ok, I think that wojox solution will help me, but can I find that folder in which are stored those packages so I can just copy them to some other storage hardvare without having to download them again.

You would have to download them again with what I linked you to.

Try looking in /var/cache/apt/archives.

---

