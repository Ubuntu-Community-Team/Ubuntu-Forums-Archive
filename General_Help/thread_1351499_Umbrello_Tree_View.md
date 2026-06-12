---
title: "Umbrello Tree View"
date: 2009-12-10
forum: General Help
---

### Post by michaels23 on 2009-12-10
I seem to have made my tree view disappear in Umbrello. I can't find any way to restore it. Can anyone tell me where I should be looking?
 
Thanks in advance.

---

### Post by santiagobasulto on 2010-05-27
You should remove your umbrello config file. Back it up first. A better way should be to know what config change the views. So, the simple solution:

1) Locate your config file: usually in  /home/<YOUR-NAME>/.kde/share/config/umbrellorc
2) Back it up: cp umbrellorc umbrellorc.backup
3) Remove it: rm umbrellorc
4) Start umbrello: umbrello
5) Close umbrello
6) A fresh new config file was created.

I hope this helps you!

---

