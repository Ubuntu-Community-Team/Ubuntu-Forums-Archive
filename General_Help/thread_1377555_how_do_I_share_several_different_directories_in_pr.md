---
title: "how do I share several different directories in proftpd"
date: 2010-01-10
forum: General Help
---

### Post by Eugene_Bondarenko on 2010-01-10
hi, I've installed proftpd and gadmin-proftpd. in gadmin-proftpd I've set a user with the home directory /home/ftp/incoming. Then I went to gadmin and added another directory I want to share: /media/Y. When I sign in to FTP, I get to my home directory (/home/ftp/incoming)...but how do I get to /media/Y now?

---

### Post by gsmanners on 2010-01-10
I think for security reasons, proftpd doesn't allow symlinks. One way around this is to use bind mounts. That is:

```
mount --bind /media/Y /home/ftp/incoming/Y
```

---

### Post by Eugene_Bondarenko on 2010-01-10
Thanks for the answer! If I set that command to be executed at startup, will I still be able to access stuff using old URL? Y is my main backup HDD and a lot of stuff accesses it via /media/Y

---

### Post by gsmanners on 2010-01-10
The bind option just mirrors the data, so no problem. If you want it set up at startup, you should really use an /etc/fstab entry:

/olddir  /newdir  none  bind

---

