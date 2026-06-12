---
title: "&quot;Not authorized to make changes&quot; to users and groups in Ubuntu 9.10"
date: 2010-02-01
forum: General Help
---

### Post by gglaser on 2010-02-01
I am using Ubuntu 9.10, and I want to modify user privileges / properties. When I go to System -> Administration -> Users and Groups, the key button is grayed out. Next to it is the message "Not authorized to make changes." The "User Privileges" tab is grayed out for myself, and I should be an admin user. In doing some searching, it seems that perhaps this is a limitation of 9.10. I am wondering if anyone has found a way around this? I know the terminal commands for adding and deleting a user, but what about changing permissions? The reason I am trying to change my permissions is to add me to "plugdev" so I can access my SD card. Any help would be appreciated, thanks!!

---

### Post by Leppie on 2010-02-01
you can use the adduser command to add users to groups:
```
sudo adduser <username> fuse
```

---

