---
title: "sudo"
date: 2009-11-12
forum: General Help
---

### Post by Bladergroen on 2009-11-12
A colleague recently installed Xubuntu 9.04 in an extreme basic configuration. For example there is not a GUI to the network settings.
To activate a second login account I used the command "adduser postgres", because I need to start a postgresql server. This account has basic rights. The only other account has sudo rights.
Now when I login into the postgres account from startup and need to perform a sudo command with "sudo -u blabla", the postgresql password is asked in stead of the blabla password. When typing the pgsql password it is rejected of course because it is not a sudo account.
Please help on this subject, I'm not really a newbe, but not really experienced either.

---

### Post by Giblet5 on 2009-11-12
In order to use sudo, a user must be configured in /etc/sudoers, or be a member of a group that is configured in /etc/sudoers.

Admins are added to the "admin" group, and the "admin" group is configured in /etc/sudoers.

It's elegant and powerful...

Regular Joes (aka l'users) are not in the "admin" group. Heh heh. (We take our petty shadenfreudic pleasures where we can find 'em...)

The following command will add user 'postgres' to the 'admin' group, and sudo will then work for that user. Obviously, you'll have to run this from that blahblah admin user's account, cuz it requires sudo privelege.

```
sudo usermod -a admin postgres
```

Tada!

---

