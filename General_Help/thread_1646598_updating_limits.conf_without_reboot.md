---
title: "updating limits.conf without reboot"
date: 2010-12-16
forum: General Help
---

### Post by mahmoodn on 2010-12-16
I have changed and added some lines to /etc/security/limits.conf. At this time I can not reboot the system. Which service limits.conf belong to so that I can restart that service.
Thanks,

---

### Post by Wtower on 2010-12-16
Interesting question. Have you enabled pam limits? I believe they are not enabled by default on Ubuntu. Check the file /etc/pam.d/su . According to the documentation, in order to enable you need to reboot.

Apart from that, I am not sure if the changes take effect after on each su, sudo or login, but it might help with cat /proc/(pid)/limits

Regards

---

### Post by mahmoodn on 2010-12-16
> **Wtower said:**
>  cat /proc/(pid)/limits

what is (pid)?

---

### Post by Wtower on 2010-12-16
Right. Forget about that one, that meant for a single process with a given pid as (pid). Now that I think about it, it wouldn't reflect the limits for a user. My guess is that you would like to limit user mysql, wouldn't you.

---

### Post by mahmoodn on 2010-12-16
No actually I changed "open files" in ulimit. The default maximum value is 1024, I changed to 8192. However it doesn't work until I reboot the system or something else that I am looking for....

---

