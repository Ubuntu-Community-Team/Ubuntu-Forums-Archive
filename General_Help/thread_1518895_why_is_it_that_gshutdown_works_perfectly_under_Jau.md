---
title: "why is it that gshutdown works perfectly under Jaunty but will not work under Lucid ?"
date: 2010-06-27
forum: General Help
---

### Post by wpshooter on 2010-06-27
The gshutdown program works perfectly on my Jaunty computer but will not work at all on my Lucid computer.

Why is that ?

Thanks.

---

### Post by dr_smit on 2010-09-23
same problem here needs attention!!!

---

### Post by MooPi on 2010-09-23
I have a solution but it doesn't include gshutdown. I create a cronjob something like this for today at 11:00am  ```
00 11  23  09  *  sudo shutdown -h now
``` You can specify any time or date.
The tricky part is I've edited my sudoers file to give me privileges for shutdown without entering my password.
This line at the end of your sudoers, ```
%username ALL=(ALL)NOPASSWD:/sbin/shutdown
``` The /etc/sudoers file should only be edited with ```
sudo visudo
```An incorrect edit of your sudoers file could render your system inoperable so use caution and double check your changes.

---

