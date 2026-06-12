---
title: "files shared between users"
date: 2009-09-01
forum: General Help
---

### Post by majoob on 2009-09-01
I'm configuring our new computer...
How do I set things up so two (or more) users can have a "shared" area or folder to read and write common data files, without getting tripped up in permissions hell?

For example, photos downloaded from a camera, mp3's ripped from CD's, email attachments, docs, spreadsheets, etc. If photos were downloaded from one profile, they were read-only to the other.

---

### Post by P4man on 2009-09-01
right click the folder you want to share, go to properties, permissions, give the "others"  read/write permission if thats what you want ;)

---

### Post by CaesarLike on 2009-09-01
If you wanted to get serious about it, maybe you could have a separate partition for these files, format it with FAT32, and mount it as users,rw,exec,umask=000. (I think these would work for a Fat32 partition).  If I remember right a FAT32 partition will then allow any user to access the files as it does not use linux file permissions.  Anyway just an idea. :)

---

### Post by majoob on 2009-09-02
Thanks for the replies. 

I added /home/data, the owner of the data folder is root but I changed the group to "users" and gave users rwx permissions. I left "Others" as read-only.

Think that'll work?

---

### Post by majoob on 2009-09-02
(Nope) Aren't all users members of the "users" group?

---

