---
title: "When Installing Multiple Packages, Skip Packages That Can't Be Installed?"
date: 2011-09-24
forum: General Help
---

### Post by dniMretsaM on 2011-09-24
I was wondering if there was a way to make apt-get skip an uninstallable package (no installation candidate or what ever) and continue installing the others. The reason I'm wondering this is that I'm writing a script that will make the changes I want to my computer after I do a fresh install of 11.10. If I were just making it for myself, it wouldn't really be a problem since I could just edit the script to correct the error, but I'm considering making it so that another user could enter what they want to install, and then automatically generate the script for them to run. But if I gave all the packages to apt-get in one command and one of them happened to be spelled wrong, that would cancel the whole installation process. One solution would be to give each package a separate command, but that would be a pain. I suppose I could do a loop, but still. So anyway to do what I want? I'm writing this in Python BTW.

---

### Post by dniMretsaM on 2011-09-25
Bump.

---

### Post by dniMretsaM on 2011-09-30
Bump.

---

### Post by dniMretsaM on 2011-10-02
Bump.

---

### Post by dniMretsaM on 2011-10-04
Oh the monotony... Someone has to know the answer to this (even if that answer is "not possible").

---

### Post by dniMretsaM on 2011-10-05
*twiddles thumbs*

---

### Post by mcduck on 2011-10-05
Like "man apt-get" would have told you, apt has a "--ingore-missing" option which makes it skip any missing packages and work around the problem the best way it can.

Of course if any other package depends on the missing packages you may end with quite a many packages that won't get installed.

---

### Post by dniMretsaM on 2011-10-05
> **mcduck said:**
> Like "man apt-get" would have told you, apt has a "--ingore-missing" option which makes it skip any missing packages and work around the problem the best way it can.

Of course if any other package depends on the missing packages you may end with quite a many packages that won't get installed.

Man pages, "Duh!" I always forget about man pages until someone mentions them. I really (really, really) need to think to use those. I'll consider this a lesson. Thanks.

---

