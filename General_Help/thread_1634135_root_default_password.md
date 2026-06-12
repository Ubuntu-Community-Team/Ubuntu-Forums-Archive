---
title: "root default password"
date: 2010-11-30
forum: General Help
---

### Post by big136 on 2010-11-30
Hi,
what is root default password on ubuntu 7.4 ?

Thank you.

---

### Post by nothingspecial on 2010-11-30
There isn`t one.

You use sudo instead.

---

### Post by sisco311 on 2010-11-30
By default, the root password is locked. See: [uhelp]community/RootSudo[/uhelp]

---

### Post by Goldfissh on 2010-11-30
Use Sudo to run things as root. You then enter your password (whatever you set it to be), and then you can run whatever you want.

---

### Post by big136 on 2010-11-30
thanks. Be so kind to give me the syntax :
user1@ubuntu:~/vmwaretools/vmware-tools-distrib$ ./vmware-install.pl
Please re-run this program as the super user.

Execution aborted.

Found VMware Tools CDROM mounted at /media/cdrom0. Ejecting device /dev/hdc ...


user1@ubuntu:~/vmwaretools/vmware-tools-distrib$ sudo 
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
user1@ubuntu:~/vmwaretools/vmware-tools-distrib$ sudo  vmware-install.pl
Password:
????? 
Then it asks me password.

---

### Post by sisco311 on 2010-11-30
```
sudo ./vmware-install.pl
```

---

