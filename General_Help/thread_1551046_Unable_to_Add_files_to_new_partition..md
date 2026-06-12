---
title: "Unable to Add files to new partition."
date: 2010-08-11
forum: General Help
---

### Post by imfreak130 on 2010-08-11
I am Dual-booting Windows 7 and Ubuntu. 


Before installing Ubuntu, I made 2 Partitions, One for Ubuntu, and one for Sharing between Windows 7 and Ubuntu. 


After filling the Sharing folder up, I decided I needed to make another partition to fit my music on (25gb) (AND SHARE BETWEEN WIN7 AND UBUNTU), but I am unable to add anything to that partition. After discovering this, I attempted to change the permissions, but I do not have ownership of the partition. I attempted to use the following command:

> sudo chown username:usergroup /media/harddriveBut that did not seem to work either.

---

### Post by warddr on 2010-08-11
You can use this command:
> 
chmod 777 /media/harddrive 			 		
to give everyone read and write access to your partition.

---

