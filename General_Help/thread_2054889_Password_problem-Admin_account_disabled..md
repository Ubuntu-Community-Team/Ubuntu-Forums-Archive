---
title: "Password problem-Admin account disabled."
date: 2012-09-08
forum: General Help
---

### Post by Royalist on 2012-09-08
I am unable to change my password even in root (recovery mode), or to unlock it. I can still access my account, but without password protection. In GUI Administrator account 'disabled' is displayed.

This is what I have done so far:

In root:#```
 usermod -U roy
usermod:cannot lock /etc/passwd; try again later

~#<passwd roy
Enter new Unix password:done
Retype new Unix password:done
passwd:Authentication token manipulation error
passwd:password unchanged

passwd -a -S
roy L 09/05/2012 0 99999 7 -1

passwd -d roy
passwd:cannot lock /etc/shadow; try again later
```Two days later again root shell:

```
<mount -o rw,remount /

chmod 0440 /etc/sudoers
ls -l /etc/sudoers
-r--r----- 1 root root 574 2011-09-11 (todays date is 2012-09-07).
```I think that I have to admit that "I am in out of my depth".

Would anyone please help??

---

### Post by cryptotheslow on 2012-09-08
When trying to reset the password via the Recovery mode did you remember to 
```
mount -o rw,remount /
```

before using the passwd command?

---

