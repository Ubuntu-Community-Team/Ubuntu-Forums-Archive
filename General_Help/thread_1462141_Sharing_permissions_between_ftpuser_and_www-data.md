---
title: "Sharing permissions between ftpuser and www-data"
date: 2010-04-25
forum: General Help
---

### Post by Eax.exe on 2010-04-25
Hi there :)
I'm trying to run my own little host for fun (yes I know the implications and crappy bandwidth is a problem but that's a problem I will deal with later).

The problem is that I want BOTH the apache-user "www-data" and the ftp-user "ftpuser".
I want both to be able to read/write on the folders I make for each user.
Is there a way to do this?

Thanks in advance :)

---

### Post by Eax.exe on 2010-04-25
Does someone know this? :)
I was considering putting both in a group and then setting the group permissions, but I don't know if that would work..

---

### Post by Eax.exe on 2010-04-26
I tried ```
sudo chmod -R g+rwx users/
```
to no avail :(
(users/ is the directory I wish to apply this to.

Can anyone help? :)

---

### Post by Eax.exe on 2010-04-28
Anyone?

---

### Post by atroc on 2010-05-04
I'm kind of in the same boat.  I've added my user to the www-data group, and the account still isn't able to delete anything apache created.  If I create stuff myself via ftp (using the same account), both apache and the account can delete/access it.  Ugh!

---

### Post by Eax.exe on 2010-05-05
Can anyone help? :)

---

### Post by JKyleOKC on 2010-05-05
I haven't tried exactly what you are asking, but it's the general principle behind the "group" existence.

I've added myself to the www-data group, then changed the permissions on the /var/www directory (recursively) from the group being read-only to it being read-write, and have no problem maintaining files in that directory and its subdirectories while logged in as myself.

I would try adding "ftpuser" to the "www-data" group and vice versa, changing the group permissions from read-only to read-write in the affected directories, and see whether that does what you need. My own ftp server uses "nogroup" as the group owner of its home directory, and my apache2 is on a different machine, so I can't try it here, but it ought to work. The whole purpose of the "group" thing is to allow a selected collection of individuals independent access to a directory, a directory tree, or specific files, with different permissions than those granted to the world at large. The *buntu practice of setting group and world permissions both to "read-only" in many cases tends to obscure that purpose somewhat...

---

