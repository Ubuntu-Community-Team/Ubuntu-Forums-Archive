---
title: "Windows locks files on Samba share"
date: 2012-03-01
forum: General Help
---

### Post by laxmankk11 on 2012-03-01
My ubuntu box is a media server for my house. I run jdownloader from my windows 7 laptop, and it downloads files to the jdownloader folder on ubuntu. After the files download I move them out of there and into another folder (Movies, Music, Software, etc..) where they stay. The problem I'm having is that when the files download to the inital jdownloader folder, they are locked. Ubuntu is not the owner of the files, the Windows PC is so when I want to move them I have to either chmod the files or do them from my laptop which takes forever. Can anyone point me in the right direction here?

---

### Post by Paddy Landau on 2012-03-02
What do you mean by "locked"? Do you mean that the permissions are set to read-only, like this:
```
*ls -l*
-r--r--r-- 1 nobody nogroup    0 2012-03-02 16:39:58 locked.file
```

---

