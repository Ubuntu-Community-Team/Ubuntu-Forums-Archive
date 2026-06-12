---
title: "single line login on mySQL"
date: 2011-04-05
forum: General Help
---

### Post by duckyq on 2011-04-05
Hi all, is there any commands on mySQL that works similarly to ```
"echo ubuntu | sudo -S su -c 'cat /etc/passwd'"
``` allowing me to remotely access mysql along with the password so i can login mysql without the need of entering the password
 
Solved: mysql -h 192.192.192.1 -u ubuntu -pPASSWORD

---

