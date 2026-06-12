---
title: "Changing my username to something else"
date: 2012-10-04
forum: General Help
---

### Post by rmcellig on 2012-10-04
I am using Xubuntu 12.04.

These are the instructions I will be using to change my user name:

[http://www.liberiangeek.net/2010/08/change-rename-username-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/08/change-rename-username-ubuntu-10-04-lucid-lynx/)

I will post back once I am in root because I was having a problem changing my username. More to come...

---

### Post by rmcellig on 2012-10-04
When I try to change my username, this is what I get:

root@xubuntu1204-3:~# usermod -c "randy" -l randy home
usermod: user home is currently logged in
root@xubuntu1204-3:~# 

What am I doing wrong? I look up at the upper right hand corner of my screen and it says root.

---

### Post by rai4shu2 on 2012-10-04
That guide you're using is outdated, and uses some questionable methods. I would suggest locking the root account (passwd -l root) and using the following guides:

[https://help.ubuntu.com/12.04/ubuntu-help/user-add.html](https://help.ubuntu.com/12.04/ubuntu-help/user-add.html)
[https://help.ubuntu.com/12.04/ubuntu-help/user-admin-change.html](https://help.ubuntu.com/12.04/ubuntu-help/user-admin-change.html)
[https://help.ubuntu.com/12.04/ubuntu-help/user-delete.html](https://help.ubuntu.com/12.04/ubuntu-help/user-delete.html)

Add a new user with the correct information, change that user to have admin privilege, then delete the old account.

EDIT: Make sure you have backups of anything you need from the old account, first.

---

### Post by rmcellig on 2012-10-04
Thanks so much. This makes way more sense to me.

---

