---
title: "Emergency......"
date: 2011-10-25
forum: General Help
---

### Post by raja.genupula on 2011-10-25
Any of my hard disk partition not showing,i mean missed in my file-manager . its not showing them . Now i am in Ubuntu 11.10.

 ```
assassin@assassin-ubuntu:~$ sudo blkid
/dev/sda1: UUID="e683bdd4-31dc-403d-9d6b-84712bacfd5d" TYPE="ext4" 
/dev/sda3: LABEL="New Volume" UUID="061F37EF05F98924" TYPE="ntfs" 
/dev/sda4: LABEL="alls" UUID="4CED98D85382CF98" TYPE="ntfs" 
/dev/sda5: LABEL="softwares" UUID="2CC08081C080534E" TYPE="ntfs" 
/dev/sda6: LABEL="XUbuntu 11.10" UUID="05b5dced-7e03-4afd-a8ec-10fae28baad7" TYPE="ext4" 
/dev/sda7: UUID="331c80a5-54ea-4997-8e45-de267e1e41d3" TYPE="swap" 
/dev/sda8: LABEL="43 GB" UUID="ca51774a-a607-4cc8-96e4-c4d924e616f6" TYPE="ext4"
```

---

### Post by papibe on 2011-10-25
Hey raja.genupula. It sounds scary.

Are they visible using 'df' and 'sudo fdisk -l'

Regards.

---

### Post by raja.genupula on 2011-10-25
A blind choice of restart corrected the problem.

but i am wanna know , why ?

---

### Post by raja.genupula on 2011-10-25
> **papibe said:**
> Hey raja.genupula. It sounds scary.

Are they visible using 'df' and 'sudo fdisk -l'

Regards.

Hi papibe
           Hope you're doing good.Before restart,df -h given the output as only filesystem. But why restart solved this ? whats the reason ?

---

