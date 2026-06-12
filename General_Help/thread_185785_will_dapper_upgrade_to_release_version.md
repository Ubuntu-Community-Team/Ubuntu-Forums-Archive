---
title: "will dapper upgrade to release version"
date: 2006-06-01
forum: General Help
---

### Post by edifuzzy on 2006-06-01
Damn this site is getting humped today....


Now to the question...
I have been a dapper user/tester for about 6 weeks or more now. Should I do a fresh install with a proper Release disk or will my Dapper automatically upgrade the vital components to release versions? 
i think it will upgrade but not too sure....

On a different subject....anyone know how to get rid of Kdocker.....Looks nice but is pissing me off now!!

---

### Post by edifuzzy on 2006-06-01
Don't bother answering...have found my answer..

sudo apt-get update
sudo apt-get distro upgrade    or something along those lines..

---

### Post by yaztromo on 2006-06-01
I have a beta version of Dapper installed.

Could someone clarify...

Do I just apt-get upgrade or do I have to apt-get dist-upgrade?

---

### Post by Hezekiah on 2006-06-01
You should probably do a "apt-get dist-upgrade" first, and then you can use the update-manager or a plain "apt-get upgrade" to keep up with security/bug fixes and whatnot for Dapper now that it has gone stable.

---

### Post by sc3252 on 2006-06-01
it wont hurt you to do both, unless you edited your sources to include etch.  I doubt it though.

---

