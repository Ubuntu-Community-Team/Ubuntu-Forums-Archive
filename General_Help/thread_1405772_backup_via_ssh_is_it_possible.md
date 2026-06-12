---
title: "backup via ssh is it possible ?"
date: 2010-02-13
forum: General Help
---

### Post by ibrahim.k on 2010-02-13
Hi,
I have ubuntu 8.4 
can i backup or clone the system daily using ssh ??

thnx in advance

---

### Post by r_s on 2010-02-13
Yeah, there are tools that can do that , just google it.

---

### Post by ibrahim.k on 2010-02-13
thnx [r_s]("http://ubuntuforums.org/member.php?u=915274") i have searched at this forum for the title (backup) but it wasn't useful i will try using google anyway :)

---

### Post by HermanAB on 2010-02-13
Howdy,

You need to read up on rsync.  <what you need to do is install ssh-server and rsync packages, then connect like this:

rsync -e ssh /from/path server:/to/path

---

