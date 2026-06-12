---
title: "Scanner not available to all users 12.04 LTS"
date: 2012-05-03
forum: General Help
---

### Post by Koura on 2012-05-03
In previous Ubuntu OS I had to copy the firmware file for my Genius Color Page Slim into user/share/sane/gt68xx to get it to work.

In 12.04 Simple scan would not work. I found no Sane folder so downloaded Xsane from Ubuntu software centre but found that there was no gt68xx folder. 

As Root (permission otherwise denied) I then used MC to copy the gt68xx folder containing the firmware file from my Ubuntu 10.10 system into the Sane Folder.

Both Simple scan and Xsane both now work using the Administrator account but the Standard user account cannot find the scanner.

Can anyone help please?

---

### Post by PaulEdwards on 2012-08-08
Ensure access to the firmware is granted to all users of the system by issuing this command:

sudo chmod 644 /usr/share/sane/gt68xx/*.fw


```
kimberly@kimberly-desktop:/usr/share/sane/gt68xx$ ls -lh
total 24K
-rw-r--r-- 1 root root 8.0K 2012-02-15 18:50 cism216.fw
**-rwx------** 1 root root 8.0K 2012-08-07 21:29 cism603.fw

kimberly@kimberly-desktop:/usr/share/sane/gt68xx$ **sudo chmod 644 *.fw **
kimberly@kimberly-desktop:/usr/share/sane/gt68xx$ ls -lh
total 24K
-rw-r--r-- 1 root root 8.0K 2012-02-15 18:50 cism216.fw
**-rw-r--r--** 1 root root 8.0K 2012-08-07 21:29 cism603.fw
```

---

