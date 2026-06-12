---
title: "Python shutil over local network"
date: 2010-08-20
forum: General Help
---

### Post by Andrew1234 on 2010-08-20
Hi I am trying to copy a file over from a xp box to my ubuntu 10.04 over a local network using python's shutil module. I can use this script windows to windows without problems but if I try from my ubuntu box I get:
> 
IOError: [Errno 2] No such file or directory: '/server/a_folder/17-08.TXT'


```
import shutil
src = '/server/a_folder/17-08.TXT'
des = '/home/user/Desktop/a_text_file.txt'
shutil.copyfile(src,des)
```

The server has been mounted and I can transfer files manually and permissions on the fire wall is allowed connections. Any ideas ?

---

