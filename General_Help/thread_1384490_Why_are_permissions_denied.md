---
title: "Why are permissions denied?"
date: 2010-01-18
forum: General Help
---

### Post by Silvernail on 2010-01-18
> dave@dave:/var/spool/cron$ sudo dir crontabs
[sudo] password for dave: 
dave  root
dave@dave:/var/spool/cron$ ls -l
total 12
drwxrwx--T 2 daemon daemon  4096 2009-10-28 16:02 atjobs
drwxrwx--T 2 daemon daemon  4096 2009-09-15 08:09 atspool
drwx-wx--T 2 root   crontab 4096 2010-01-18 10:39 crontabs
dave@dave:/var/spool/cron$ cd crontabs
bash: cd: crontabs: Permission denied
dave@dave:/var/spool/cron$ sudo cd crontabs
sudo: cd: command not found

Is this caused by something I have set wrong?

I can successfully do:
```
sudo cat crontab/dave
```

---

### Post by phillw on 2010-01-18
> **Silvernail said:**
> Is this caused by something I have set wrong?

I can successfully do:
```
sudo cat crontab/dave
```

Hi,

Your system and you are behaving perfectly well.

as a user you should not have access to, nor be able to alter those files (amongst hundreds of others). That is why you see the error.

Using sudo makes you a **s**uper **u**ser  It is one of the reasons to be careful with sudo - you remove the line of protection that reads "You don't *really* want to kill your system, do you ?"  

It is worth the time to read this --> [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards,

Phill.

---

### Post by michy99 on 2010-01-18
According to this```
drwx-wx--T 2 root crontab 4096 2010-01-18 10:39 crontabs
```only root has read access. It's set the same on my system, so that must be the way it's supposed to be. Make yourself root with```
sudo -i
``` and you can do what you need. Just be careful you don't mess anything up.

---

### Post by mikewhatever on 2010-01-18
No, nothing wrong there. Crontab is owned by root and only root has the read permission.

---

### Post by Silvernail on 2010-01-18
Thanks for all the feedback.

This denial of permissions  has happened to me before and yes I was deep into the system. Areas that I should not be.

Thanks again.
Dave

---

