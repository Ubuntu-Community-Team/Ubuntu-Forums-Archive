---
title: "Network Drive Problems Driving Me Crazy!!!"
date: 2009-11-07
forum: General Help
---

### Post by Tman5293 on 2009-11-07
Ok so here is the deal...

I have an external hard drive that I would like to make a network drive on my Ubuntu machine. So I made the drive a share on samba because this drive needs to be shared between two Windows computers and the Ubuntu one I'm mounting it on. Anyway, I made it a share in samba and it shows up on my Windows computers but when I try to open the drive I get an error telling me that I do not have the permissions to open it and that network access is denied. So I went back to my Ubuntu machine to change the drive's permissions. The problem is that when I try to change the permissions even with root powers it tells me 

"The group could not be changed. You do not have the permissions necessary to change the group of "74CC-4963"."

It wont let me change any of the permissions for the drive and all of them result in the same error.

Please help I have no idea what to do!

---

### Post by doas777 on 2009-11-07
are you using a username recognized by the server?
I have to add each user to samba rights by creating the user and running:
```
sudo smbpasswd -a <username>
```

---

### Post by Ocxic on 2009-11-07
google "webmin" it helps with configuring samba as well as most other things for the computer, no need to edit config files, and is much easier.

---

### Post by Tman5293 on 2009-11-07
> **doas777 said:**
> are you using a username recognized by the server?
I have to add each user to samba rights by creating the user and running:
```
sudo smbpasswd -a <username>
```

I have a program to manage samba and I have it set to allow access to anyone on the network

---

### Post by Tman5293 on 2009-11-07
Bump!!!!! I really need this drive! Please help!

---

