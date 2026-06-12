---
title: "Backing up files and avoid problems with permissions later"
date: 2010-02-09
forum: General Help
---

### Post by thegeezer3 on 2010-02-09
I have some very important programming files I want to backup before I reinstall my 9.04 ubuntu from the 9.10 (its causing me all sorts of problems).

The files size is small so im just going to copy them over to dropbox. Im wondering, when i reinstall ubuntu will there be any issues re the permissions of those files because my old user account which created them and the new user Ill setup on the new install will be different?

---

### Post by warfacegod on 2010-02-09
Using the same username and password *ought* to resolve possible permissions conflicts.

---

### Post by rnerwein on 2010-02-09
hi
note: names are sonic and reek
what must be the same to give you full access (permissions) to your files are user- and group-id (numeric) !
ciao

---

### Post by louieb on 2010-02-09
Just make sure the backup copy allows for others to read.
When a user copies a file owned by another user the user that did the copy becomes the copies owner. 

i.e.. sam owns /backup/xyz.txt 

joe copies /backup/xyz.txt to /home/joe 

joe owns /home/joe/xyz.txt.

---

