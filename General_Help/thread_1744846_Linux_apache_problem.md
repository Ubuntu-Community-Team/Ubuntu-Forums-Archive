---
title: "Linux apache problem"
date: 2011-04-30
forum: General Help
---

### Post by bender1 on 2011-04-30
.I want to host a website on my pc.i have w7 and ubuntu 9.10 in a Vbox.I put website files in /var/www it was all good i tested it was working ,but then i changed the files ,to change the look ,but when i connect to site it the same no changes,what do i need to do ?

---

### Post by dylbud on 2011-04-30
I sometimes have troubles with stuff appearing correctly because when I put them in /var/www Apache changes the permission settings.

Your problem doesn't sound exactly like ones I've dealt with, but you might want to try check those permissions.

Right click on the files in question, and make sure permissions are set to at least "read" for owner, group, and other.

---

