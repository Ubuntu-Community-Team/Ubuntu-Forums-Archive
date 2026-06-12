---
title: "sudo"
date: 2009-08-30
forum: General Help
---

### Post by wurm on 2009-08-30
i have added another user. how can he make use of sudo ?

---

### Post by Elfy on 2009-08-30
[https://help.ubuntu.com/community/RootSudo#Users](https://help.ubuntu.com/community/RootSudo#Users)
> 
To add a new user to sudo, open the Users and Groups tool from System->Administration menu. Then click on the user and then on properties. Choose the User Privileges tab. In the tab, find Administer the system and check that.

---

### Post by slakkie on 2009-08-30
man sudo
man sudoers

If you want him to give the same rights as you, then you should add him in the admin group

sudo nano /etc/group 

add the user name to the group admin.

---

### Post by wurm on 2009-08-30
ok, i found it
sudo adduser <username> admin
thank you

---

