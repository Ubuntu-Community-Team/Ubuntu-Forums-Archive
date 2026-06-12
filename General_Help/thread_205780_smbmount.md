---
title: "smbmount"
date: 2006-06-29
forum: General Help
---

### Post by metallcoholix on 2006-06-29
Hi, im trying to mount a volume in samba, my windows computer is under the network home, the name is metallcoholix and the folder is documents c. I created a dir /home/metallcoholix/windows. When I type in the terminal:
smbmount //metallcoholix/documents \c /home/metallcoholix/windows a message appears saying "smbmnt must be installed suid root for direct user mounts"
Any help here???

Thx

---

### Post by scxtt on 2006-06-29
i'd try "documents\ c" before anything else ... or "documents_c" as the share, rename it on the windows box ... spaces are bad news IMO ...

---

### Post by danik on 2006-09-14
hi

i've tried to mount the directory that are in a windows xp system with the comand smbmount, after the configuration of samba for my LAN. There's only one problem: i don't know my windows username e my windows password! I've never given any password to my win operation system, but if i don't write anything after "Password:" it doesn't work.
The username could be "Administrator", but how can I find the correct password???

Thank's for help,

dNk

---

### Post by tsumi on 2007-01-04
to my understanding the default xp password is not. that is to say, its not "blank" but there is just no password which might explain why a blank password would not work.

my advice would be to login to the xp machine as "administrator" with no password. once logged in hit ctrl+alt+del and set a password then use that password in your smbmount string.

hope this helps.

---

