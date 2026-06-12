---
title: "Samba's new account dont work"
date: 2010-05-20
forum: General Help
---

### Post by Timothytech on 2010-05-20
SO i made a server with ubuntu 10.04. 

I created 3 new accounts on the linux then made identical samba accounts to match. For some reason when i input the information to log into a shared directory it doesnt work. my original login works fine, 

```


[JediServer]
path = /home/timothy/jediServer
pulbic = yes
browseable = yes
read only = no
valid users = timothy, manager1, manager2
guest ok = no



```

not sure why it doesnt work, i logged into the server with my other accounts. is there a step im missing?

---

### Post by cariboo on 2010-05-20
Have you created the accounts and enabled them?

```
sudo smbpasswd -L -a user
```

to add the user, and to enable the user:

```
sudo smbpasswd -L -e user
```

---

