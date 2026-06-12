---
title: "running system command without sudo"
date: 2009-12-02
forum: General Help
---

### Post by championboxes on 2009-12-02
How can I run this command without the use of sudo?

```
/usr/sbin/iwconfig wlan0 | grep 'Link Quality' | sed 's/.*Link Quality=*:*\([0-9]*\).*/\1/'

```

Would I have to change the permissions of /usr/sbin/iwconfig?
```
chmod 700 /usr/sbin/iwconfig
``` 
if that works could it cause security or other problems?

---

### Post by endBc on 2009-12-02
```
%admin ALL=NOPASSWD: /usr/sbin/iwconfig

```

Add it to your [sudoers file]("https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File") and use sudo without the need for password.

---

