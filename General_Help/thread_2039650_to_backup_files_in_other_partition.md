---
title: "to backup files in other partition"
date: 2012-08-09
forum: General Help
---

### Post by wiame on 2012-08-09
Hello, 

i would like to use backup-manager packet to store some files in an other partition but i don't know what is the value to give the this variable BM_REPOSITORY_ROOT.

there is the configuration of partitions :

/dev/sdb1   /
/dev/sda5 /home
/dev/sda1  none


the files that i would like to store are in /home/server/share

 i don't know in witch partitons the file /home/server/share is located. i would like to know also what value to give to BM_REPOSITORY_ROOT to make the storage to be in the other partition.

thank you fo your help.

---

### Post by 2F4U on 2012-08-09
Since /dev/sda5 is mounted in /home, I would assume that /home/server/share is on /dev/sda5, unless you have mounted another filesystem under /home/server/share. From the information you give only you can answer that question.

---

### Post by wiame on 2012-08-09
thank you for your quick answer
there is no partition partition mouted at /home/server/share

but since sdb1 is mounted at / , we we can't consider that the files /home/server/share is also located in sdb1?

alse whaat is the value to give to BM_REPOSITORY_ROOT to backup in sdb1?

thank you

---

