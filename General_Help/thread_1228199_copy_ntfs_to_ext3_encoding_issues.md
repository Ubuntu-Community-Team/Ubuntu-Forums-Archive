---
title: "copy ntfs to ext3 encoding issues"
date: 2009-07-31
forum: General Help
---

### Post by cscj01 on 2009-07-31
I have moved my MySQL databases from XP SP3 to Ubuntu 9.04. I used MySQL Administrator Backup and Restore to move them. The data bases moved fine.  None of my queries that I used in XP run under Ubuntu. I get a 1064 on all of them. I can create new queries from scratch, but the ones I copied over do not work. Any ideas?

Could this have anything to do with encoding? I copied the queries, which are of type qbquery, from an NTFS volume to an ext3 volume using Nautilis. The backup scripts are type sql, and the scripts created the databases and restored the data. So the scripts were okay as far as Ubuntu was concerned. But the queries seem to all cause the parsing error from the get go. I do have ntfs-3g installed, but I am loading the queries into Query Browser from the copies on the ext3 volume. Hmm.

Some additional info.

On Ubuntu, I have MySQL Query Browser 1.2.12, MySQL Administrator 1.2.12, MySQL Server 5.0.75, and MySQL Client 5.0.75.

On XP, the MySQL Administrator version I used to backup the databases is 1.4 and the server is 5.0.77

---

