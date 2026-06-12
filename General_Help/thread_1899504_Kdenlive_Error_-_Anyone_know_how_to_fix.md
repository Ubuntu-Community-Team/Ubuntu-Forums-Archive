---
title: "Kdenlive Error - Anyone know how to fix?"
date: 2011-12-23
forum: General Help
---

### Post by JF382 on 2011-12-23
Fatal error

MLT's SDL module not found

^^ That is what I get when I try to launch Kdenlive, does anyone know how to fix this? Thanks, I appreciate anyone who answers.

---

### Post by Majgeek on 2011-12-24
I had the same problem, and found the following.   While the following is not a perfect fix, since you can't re-run the config wizard later or you will get the same error, this will get kdenlive running.   I am sure there is a better way.

Create the file "kdenliverc" in your home folder 

ie ~/.kde/share/config/kdenliverc


Edit the file and add the following

[version]
 version=0.8

---

