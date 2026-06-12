---
title: "Restore home directory?"
date: 2010-01-06
forum: General Help
---

### Post by VeskoJl on 2010-01-06
I deleted my /home directory. Is there a way to recreate it. I tried just to make new home folder and then add new user, but still can't login. Don't need to restore the data.

---

### Post by Leppie on 2010-01-06
if you don't need to restore your data, you can try removing and then re-adding your account:
```
sudo deluser <username>
sudo adduser <username>
```

if this is your main account, you may want to use the useradd command to re-add your account:
```
sudo useradd -u 1000 -G admin,adm -m <username>
```
(this can also be done using adduser, but the command options are longer and i'm lazy... :P )
you can then set this user's password like this:
```
sudo passwd <username>
```

---

### Post by VeskoJl on 2010-01-06
The problem may be KDE. I get following error:

```
kstartupconfig4 does not exist or fails.The error code is 3
```

---

