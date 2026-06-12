---
title: "How to Change GUI enviorment?"
date: 2010-05-31
forum: General Help
---

### Post by adeee on 2010-05-31
sudo nautlius command not works. 

so how i get the root access with nautilus.

[ATTACH]158902[/ATTACH]

error shows like this,. 

bcoz file that copy in filesystem not works correctly..

i-e i copy and paste PHPBb3 in /opt/lampp/htdocs

when i run it from localhost it says you have no permission to use this file.

However localhost is already started.

Thnxs

---

### Post by dv3500ea on 2010-05-31
run
```
sudo mkdir /root/Desktop
```
then 
```
sudo nautilus
```
make sure you enter the correct password.

---

