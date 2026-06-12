---
title: "Evolution Restore-Computer Forensics may be required"
date: 2009-11-25
forum: General Help
---

### Post by gto0814 on 2009-11-25
I was running 9.04 then upgraded to 9.10 through the update manager. The system seemed slow so I prepared for a fresh install. I backed up evolution through it's backup utility which I'd done before with no problems. I copied out the archive along with other files to a 2-G micro-sd. After clean installation files restored no problem but evolution will not restore.  
 Output from Properties:  
 Name: evolution-backup.tar.gz
 Type: Tar archive (gzip-compressed) (application/x-compressed-tar)
 Size: 100.1 MB (104972617 bytes)
 Modified: Sat 21 Nov 2009 03:36:04 PM EST “ when I made backup”
 I have attempted to resolve the issue by executing [gunzip evolution-backup.tar.gz] which reports “not in gzip format”; I renamed removing .gz and executed [tar -xvf evolution-backup.tar] which reports “This does not look like a tar archive”; executed [file evolution-backup.tar.gz] which reports “DOS executable (device driver)” which would not execute on Vista partion and also attempted to unpack under Vista no luck; I executed [recover evolution-backup.tar.gz > recovery] which produced empty file; I clean installed 9.04 and evolution appeared to process the file only to drop me back into the wizard without updating; and finally re-upgraded to 9.10 through the update manage again and attempted the restore without success. I really need to recover this file as it has numerous contact information, birthday, anniversary, email address's, home/work/cell #s, spouse & children, past girl friends, not to mention the saved emails containing software license keys, 2 yrs of electronic receipts not yet entered into gnucash, and recent bid proposals. Please, I really need to recover this file, all recovery information accepted.  I realize there were a lot of ways to prevent this and I've beat myself up over this since, so please don't tell me what I should have done, I fell bad enough already, thanks, George.

---

### Post by dcstar on 2009-11-25
> **gto0814 said:**
> I was running 9.04 then upgraded to 9.10 through the update manager. The system seemed slow so I prepared for a fresh install. I backed up evolution through it's backup utility which I'd done before with no problems. I copied out the archive along with other files to a 2-G micro-sd. After clean installation files restored no problem but evolution will not restore.  
.....

And you have tried the Restore function **in Evolution**, have you?

---

### Post by SirBismuth on 2009-11-26
> **dcstar said:**
> And you have tried the Restore function **in Evolution**, have you?

This, and also, I see that a few people have had issues restoring directly off a thumb drive in Evolution, myself included.  The solution is to copy the archive to your Desktop or somewhere, and restore from there.  This worked perfectly for me.

B

---

### Post by dcstar on 2009-11-26
> **SirBismuth said:**
> This, and also, I see that a few people have had issues restoring directly off a thumb drive in Evolution, myself included.  The solution is to copy the archive to your Desktop or somewhere, and restore from there.  This worked perfectly for me.

B

Was it on a FAT formatted USB?

---

### Post by gto0814 on 2009-11-27
Thanks all for the input. Yes I did attempt to restore using Evolution's restore utility and did place the archive in various directories /home, & /documents. I pulled the brand new micro-sd straight from the package and can not remember if it was the 1st or 2nd copy but did format the media between copies. George

---

### Post by dcstar on 2009-11-28
> **gto0814 said:**
> Thanks all for the input. Yes I did attempt to restore using Evolution's restore utility and did place the archive in various directories /home, & /documents. I pulled the brand new micro-sd straight from the package and can not remember if it was the 1st or 2nd copy but did format the media between copies. George

If you have dual boot, you may want to boot up 9.04 and see if you can restore into that Evolution.

If you set up a separate /home partition, then if the data is ok in 9.04 it should also work in 9.10.

---

