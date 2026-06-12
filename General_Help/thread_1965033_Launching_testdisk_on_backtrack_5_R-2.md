---
title: "Launching testdisk on backtrack 5 R-2"
date: 2012-04-25
forum: General Help
---

### Post by VirtualLockPick on 2012-04-25
Hi guys, 

I have been passing through a little problem trying to launch testdisk on backtrack 5 R-2, it seems to not be installed (when i try to run it by typing "sudo testdisk") but when i try to install it (by typing "apt-get install testdisk") it says: "testdisk is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

any ideas of how to fix this?

thanks in advance.

---

### Post by haqking on 2012-04-25
> **VirtualLockPick said:**
> Hi guys, 

I have been passing through a little problem trying to launch testdisk on backtrack 5 R-2, it seems to not be installed (when i try to run it by typing "sudo testdisk") but when i try to install it (by typing "apt-get install testdisk") it says: "testdisk is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

any ideas of how to fix this?

thanks in advance.

You are logged in as root on BT (generally), no need to use sudo.

However BT is not supported here generally best over at BT forums

and you need to be in the testdisk directory

```
testdisk-6.9/linux/testdisk_static
```

---

### Post by techsupport on 2012-04-25
> **VirtualLockPick said:**
> Hi guys, 

I have been passing through a little problem trying to launch testdisk on backtrack 5 R-2, it seems to not be installed (when i try to run it by typing "sudo testdisk") but when i try to install it (by typing "apt-get install testdisk") it says: "testdisk is already the newest version. 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

any ideas of how to fix this?

thanks in advance.

In terminal:

```
apt-get purge testdisk
apt-get clean all
apt-get autoremove
apt-get autoclean
apt-get install testdisk
```

---

### Post by haqking on 2012-04-25
> **techsupport said:**
> In terminal:

```
apt-get purge testdisk
apt-get clean all
apt-get autoremove
apt-get autoclean
apt-get install testdisk
```

sudo is not required on BT

And its already installed according to OP, however if its not for whatever reason then its just apt-get and no sudo required

Peace

---

### Post by CharlesA on 2012-04-25
Try the backtrack forums.

---

