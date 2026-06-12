---
title: "retrieving files from root.disk"
date: 2010-06-24
forum: General Help
---

### Post by v1gorus on 2010-06-24
So I had a problem with my ubuntu 10.04 on wubi. so i saved the root.disk and uninstalled it then reinstalled unbuntu 10.04 as another partition. I did the mount thing with the root.disk and now and trying to move files over. I need permission for that and its asking me for a sudo password and i didnt set one. i tried using sudo bash and its also not working.
```

igor@igor-laptop:~$ sudo bash
root@igor-laptop:~# mv '/mnt/usr/share/themes' '/usr/share' 
mv: inter-device move failed: `/mnt/usr/share/themes' to `/usr/share/themes'; unable to remove target: Is a directory

```

---

### Post by v1gorus on 2010-06-24
isnt this easy for you guys? how do i move files with permission?

---

### Post by oldfred on 2010-06-25
You did not set a password.

With Ubuntu you have to have a password, it is part of the install and will not let you continue without one. 

You are writing into the system directory and you can only do that with sudo and your password. You also need to make sure your mount of the root.disk gives your proper permissions but I have never done that so I do not know if it is like NTFS and only set at mounting or can be changed.

---

