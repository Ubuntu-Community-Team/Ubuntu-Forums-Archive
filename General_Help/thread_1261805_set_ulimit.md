---
title: "set ulimit"
date: 2009-09-09
forum: General Help
---

### Post by premabodh on 2009-09-09
Hi All,

I tried setting ulimit but everytime I restart the system it gets reset to default value of 1024 i.e. command ulimit -n gives 1024.

Tried setting in /etc/security/limits.conf like this:
@user           soft    nofile          5000

also adding ulimit -c 5000 and ulimit -n 5000 in /etc/profile but not working.

also did 
$sudo ulimit -n 5000 
giving following error:
sudo: ulimit: command not found


Please let me know how to set this value in ubuntu 6.06 LTS. I am still using this version.

Thanks and Regards,
Vikash Anand..

:(

---

### Post by wojox on 2009-09-09
Try adding it to .bashrc:

```
gksudo gedit .bashrc
```

```
ulimit -n 5000
```

You must exit from your terminal and re-login for the change to take effect.

---

### Post by premabodh on 2009-09-09
Hi,

I tried what u suggested but it is not working.

when i restarted the system and tried command 
ulimit -n 

it gave me default value of 1024

also after login to the system when i opened the terminal it said:
bash: ulimit: open files: cannot modify limit: Operation not permitted

please let me know where am i maing mistake.

Thanks and Regards,
Vikash Anand.

---

### Post by wojox on 2009-09-09
Well then remove the line from .bashrc. See this thread:

[http://ubuntuforums.org/showthread.php?t=180127](http://ubuntuforums.org/showthread.php?t=180127)

---

### Post by premabodh on 2009-09-09
Hi,

I have googled and also found this solution and have tried it but is not working. After restarting machine when i try ulimit -n it still shows 1024.

I am not setting so high values as stated in the URL you provided. I am setting it to 4096 only which is not very high.

---

### Post by wojox on 2009-09-09
I figured it out you need to sudo su drop into root and set it 

```
ulimit -n 4096
```

Never mind as soon as you exit root it defaults back to 1024.

---

### Post by premabodh on 2009-09-09
Thanks wojox,

Thanks for your help and prompt response. This solution worked fine to me.

:guitar:

---

