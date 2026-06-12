---
title: "permissions"
date: 2010-05-24
forum: General Help
---

### Post by roflwaffle1237 on 2010-05-24
so i just installed ubuntu on my macbook pro under my win7 partition (i hope that makes sense to whoever is reading this) and i was trying to import my music from either my mac partition or my win7 partition (all my music is in both places) but it said i dont have the right permissions to view the contest.  when i tried changing the permissions it said i have to be the owner...how do i fix this? without copying my music a third time?  all help is greatly appreciated, thanks!

---

### Post by meho_r on 2010-05-26
You have to use root privileges when changing permissions. One way would be to run Nautilus as super user and change permission settings for those two folders (**WARNING: be careful when operating as root since you can destroy your system if do something wrong!**). Press Alt+F2 and type the following:
```

gksudo nautilus

```
When Nautilus opens, navigate to those folders and check their permissions (Right click on the folder > Properties > Permissions). You can check out to which "Group" every of those folders belong (and also check if members of that group have permission to access the files), then simply add yourself to that group in **System > Administration > Users and Groups > Manage Groups**.

Of course, you can change ownership of those folders too, which in case of Windows is OK, but I don't know anything about Mac and what effect will that change have on it.

Note that you may have to log out for changes to come into effect.

---

