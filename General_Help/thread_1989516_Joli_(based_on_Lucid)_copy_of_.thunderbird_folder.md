---
title: "Joli (based on Lucid) copy of .thunderbird folder"
date: 2012-05-28
forum: General Help
---

### Post by qwertyjjj on 2012-05-28
I managed to copy my .mozilla profile and it works.
However, when I copy .thunderbird, it still opens the old default even though the profiles.ini file has w4aozs4h.default in it
Also, a folder appears in the listing below but I cannot find it.
Any ideas how to get this working?

[email]j@j-jolicloud:~/.thunde[/email]rbird$ locate .thunderbird
/home/j/.thunderbird
/home/j/.thunderbird/appreg
/home/j/.thunderbird/profiles.ini
**/home/j/.thunderbird/v3f2yvnw.default**

[email]j@j-jolicloud:~/.thunde[/email]rbird$ cd /home/j/.thunderbird

[email]j@j-jolicloud:~/.thunde[/email]rbird$ ls -al
total 24
drwx------ 4 j j 4096 2012-05-28 11:42 .
drwxr-xr-x 30 j j 4096 2012-05-28 11:40 ..
-rw-r--r-- 1 j j 335 2012-05-28 11:00 appreg
drwx------ 3 j j 4096 2012-05-28 11:01 Crash Reports
-rw-r--r-- 1 j j 95 2012-05-28 12:33 profiles.ini
drwxr-xr-x 11 j j 4096 2012-05-28 12:37 w4aozs4h.default

Why does this folder /home/j/.thunderbird/v3f2yvnw.default not exist in the 2nd ls -al command?
I believe thunderbird is using this as the default folder somehow but I cannot find it.

---

### Post by wilee-nilee on 2012-05-28
Hmm, so the .thunderbird is not a hidden file in home like .mozilla and thunder are in ubuntu?

---

### Post by qwertyjjj on 2012-05-29
> **wilee-nilee said:**
> Hmm, so the .thunderbird is not a hidden file in home like .mozilla and thunder are in ubuntu?

Yes, it's hidden. That's why la -al lists them.
But why does this appear in the locate /home/j/.thunderbird/v3f2yvnw.default
but not in the ls -al
?

---

