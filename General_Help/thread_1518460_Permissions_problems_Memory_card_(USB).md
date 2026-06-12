---
title: "Permissions problems Memory card (USB)"
date: 2010-06-26
forum: General Help
---

### Post by tgomly on 2010-06-26
Hello. I have big problem. I have memory stick micro 512MB and have 300MB files in. But I don't have permission for read/write and delete files. I don't know what happened that I lost permissions. Even SUDO command didn't work

gomly@gomly-laptop:/media/900F-D016$ ls -l
total 24
drwx------ 11 gomly gomly 8192 2009-09-24 08:35 dvd
drwx------  2 gomly gomly 8192 2009-10-31 18:40 **FOUND.000**
-rwxr-xr-x  1 gomly gomly  391 2009-09-04 07:12 popers.txt

gomly@gomly-laptop:/media/900F-D016$ sudo chmod ugo+rwx dvd/ FOUND.000/ popers.txt 

chmod: changing permissions of `dvd/': Read-only file system
chmod: changing permissions of `FOUND.000/': Read-only file system
chmod: changing permissions of `popers.txt': Read-only file system
gomly@gomly-laptop:/media/900F-D016$ ls -l
total 24
drwx------ 11 gomly gomly 8192 2009-09-24 08:35 dvd
drwx------  2 gomly gomly 8192 2009-10-31 18:40 FOUND.000
-rwxr-xr-x  1 gomly gomly  391 2009-09-04 07:12 popers.txt

How can I format card,and I nead Read/Write permission?What is about FOUND.000...what(unreal thing) could create this file?

Please help

---

