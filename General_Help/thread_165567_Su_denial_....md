---
title: "Su denial ..."
date: 2006-04-24
forum: General Help
---

### Post by blssurfer on 2006-04-24
Want to execute a sudo command, change to root or use su ... Nothing all denied... Have breezy installed.. The password is the same for user and root, works in the system settings for example. 
This happend suddenly, before it worked, Must be a major bug.
Can you help?

---

### Post by gborzi on 2006-04-24
Start your system in recovery mode by pressing esc at the start of the boot to enter grub menu. You will login as root without the password request. Then check the following:
/etc/group must contain a line as
```
admin:x:106:yourusername
```
and /etc/sudoers must have this line
```
%admin  ALL=(ALL) ALL
``` If one or both of the above are missing add them and reboot to see if it works.
This thread can help in solving your problem
[http://ubuntuforums.org/showthread.php?t=159128]("http://ubuntuforums.org/showthread.php?t=159128")

---

