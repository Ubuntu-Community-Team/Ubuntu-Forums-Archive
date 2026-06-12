---
title: "Problem regarding folder protection"
date: 2010-06-22
forum: General Help
---

### Post by gaurav sontakke on 2010-06-22
Hi All 
  I want to protect my some folders from others with password 
what should I have to do ..

 I know the method of changing permission but i dont want to change the permission of that folder. I want facility like folder hide or folder security...



please help me


Thanking You 
Gaurav Sontakke

---

### Post by bkline on 2010-06-22
> **gaurav sontakke said:**
> Hi All 
  I want to protect my some folders from others with password 
what should I have to do ..

 I know the method of changing permission but i dont want to change the permission of that folder.

Then change the permission of that folder's parent:

$ mkdir ~/.private
$ chmod 700 ~/.private
$ mkdir ~/.private/folder-no-one-else-can-find

---

### Post by gaurav sontakke on 2010-06-23
thank you 
but I am searching for software which protects the folder is there any software that protects folder..??


Please suggest me any other way than changing permissions....:confused:

---

### Post by OtakuWrath on 2010-06-23
try looking for some type of encryption app

---

### Post by Rubi1200 on 2010-06-23
Available from the Ubuntu Software Center: 7zip

Allows you to create a password protected zipped file (uses AES-256 if I am not mistaken).

---

