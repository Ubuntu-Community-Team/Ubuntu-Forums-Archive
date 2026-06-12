---
title: "Task"
date: 2006-06-27
forum: General Help
---

### Post by metallcoholix on 2006-06-27
I need to create an automated task which moves a file from ubuntu to windows and from windows to ubuntu. What im trying to do is:
mv /home/Desktop/file1.txt smb://windows
However this doesnt work because the smb://windows is not a file or directory, I want to know where can I find the windows machine address or directory, or how can I perform this task.
Thx

---

### Post by woedend on 2006-06-28
have you tried using smbmount?
you must install smbfs
basically, it will mount the windows partition to a local folder of your choice (/home/windows) if you want.  Its not necessary but it's how I would approach it.  Search google for smbmount or smbfs, should find some good guides for it.

---

