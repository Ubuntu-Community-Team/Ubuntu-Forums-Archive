---
title: "SMB mounting issue"
date: 2009-11-30
forum: General Help
---

### Post by MisterNeutral on 2009-11-30
Hi Everyone,

We have an ubuntu distro that we use as an apache/mysql server for a small amount of data that is mission critical. The company is Windows based, except for the apache/mysql server, and we’re trying to run a script to copy backups of the mysql dumps and the apache web config files to our windows share. 

The command we’ve used to mount the share is as follows:

sudo mount -t cifs -o username=<USER>//server/share1$/WIKI_DO_NOT_DELETE/BACKUP /SSD_Backup

The problem is that only “//server/support1$” gets mounted, not the rest. And oddly, we can’t even browse support1$. Any advice is appreciated. 

**Note**: We have tried both the single quote trick for the directory path and using an escape tag around the $ (that is, we tried share1\$.

---

