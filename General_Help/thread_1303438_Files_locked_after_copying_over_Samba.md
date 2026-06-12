---
title: "Files locked after copying over Samba"
date: 2009-10-28
forum: General Help
---

### Post by bigred1 on 2009-10-28
I have set up my Jaunty to share folders. When I copy files to the Ubuntu machine over the LAN (anonymously, not logging in with any username), the files end up locked, e.g., for moving or deleting.

I have to run ```
sudo chmod -R 777 .
```, which is annoying.

In the settings for the folder-sharing, I give all permissions to everyone -- not safe, but it means that these problems should not occur.

How can I copy in files so that they are not locked when they arrive?

---

### Post by albandy on 2009-10-28
confiugre "create mask",and "directory mask" in smb.conf with the desired permissions.

---

### Post by Giblet5 on 2009-10-28
The file-creation mode is determined by smb.conf.

From a terminal window ```
man smb.conf
```

The mode defaults (I think) to 644, owned by user samba and group samba, so only samba can write to a file after it is created.

That's the default. You can override that with a "create mode 0666" statement.

---

### Post by Giblet5 on 2009-10-28
> **albandy said:**
> confiugre "create mask",and "directory mask" in smb.conf with the desired permissions.

Or that...

---

### Post by alphaniner on 2009-10-28
If you log in anonymously, don't files and folders get nobody/nogroup ownership?  This has happened to me anyway.

---

### Post by bigred1 on 2009-10-28
Thanks, that worked for me -- I modified *create mask *and  *directory  mask *to *0666* in *smb.conf*

---

