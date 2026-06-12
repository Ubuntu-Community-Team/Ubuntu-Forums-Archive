---
title: "fahmon lan computers"
date: 2011-12-14
forum: General Help
---

### Post by hg088 on 2011-12-14
hi!

id like to monitor my folding pc from my laptop

i use ubuntu on both of them and can mount shares with samba on both of them

both are connected to the same wireless router

so, on the laptop, inside fahmon, i click on add new client and this in the location:
```
smb://192.168.1.149/fah/
```which is the path to the fah folder on the folding pc

but fahmon show the client in black

the weird thing is that when i right click on the black client and then on viewclient files it takes me to the fah folder on the folding pc

if course, ive already checked the fah is running successfully

hope that my problem wont be to embarrassingly silly hehe

---

### Post by hg088 on 2011-12-14
solved, feel like such a noob, as usual

i didnt know that samba network folders are mounted in ~/.gvfs

just selected the fah folder on the folding pc and that was it

---

