---
title: "New Samba User Does Not Work"
date: 2010-08-29
forum: General Help
---

### Post by bennyfofenny on 2010-08-29
I want to create a samba user that will only have access to the samba shares. To do this, I used the following commands: 
```
useradd usersamba -d /dev/null -s /dev/null
passwd usersamba
usermod -a -G sambashare usersamba
smbpasswd -a usersamba
smbpasswd -e usersamba
smbd reload
```But the user will fail to log in to the samba shares. Any ideas on what could be wrong?
Thanks!

---

