---
title: "Permsions problem"
date: 2009-08-22
forum: General Help
---

### Post by Chetan26 on 2009-08-22
Hi ,
     iam working on Ubuntu 8.1 .
    When Iam  trying to take a Postgresql dump   iam getting below error.


postgres@8pmserver1:/home/serveradmin$ pg_dumpall > chetan.dmp
bash: chetan.dmp: Permission denied


Can you  help me  how to give permissions to the user and get my dump successfully.

Thanks
chetan

---

### Post by heatblazer on 2009-08-22
> **Chetan26 said:**
> Hi ,
     iam working on Ubuntu 8.1 .
    When Iam  trying to take a Postgresql dump   iam getting below error.


postgres@8pmserver1:/home/serveradmin$ pg_dumpall > chetan.dmp
bash: chetan.dmp: Permission denied


Can you  help me  how to give permissions to the user and get my dump successfully.

Thanks
chetan

Try this:
cd /home/serveradmin$ 
sudo chmod 600 chetan.dmp
or if it does not work try:
cd /home
sudo chmod 600 serveradmin

---

