---
title: "Samba Share Permissions"
date: 2010-08-27
forum: General Help
---

### Post by gavinjb on 2010-08-27
Hi,

I am trying to setup Samba to connect to my NAS drive, so far I have it connecting but normal users only have read only access, this is what I have done so far

```

mkdir /media/Data

```

Fstab
```

//192.168.2.150/Data	/media/Data	smbfs	username=username,password=password	0	0

```
I know putting the username and password in the fstab is not the best, but to start with I am trying to get everything working.

Can anyone help with what I need to do to give my normal users write access to the share?

Thanks,



Gavin,

---

### Post by lmarmisa on 2010-08-27
Add the parameters **file_mode=0777** and **dir_mode=0777** to your fstab line:

```

//192.168.2.150/Data    /media/Data    smbfs    username=username,password=password,file_mode=0777,dir_mode=0777    0    0

```

---

### Post by gavinjb on 2010-08-27
Thanks, that worked.

---

