---
title: "Loading a kernel module without asking for sudo password"
date: 2011-08-24
forum: General Help
---

### Post by ufuser01 on 2011-08-24
Hi,

I have been using the command below to insert my module, which uses the password

echo MYPASSWORD | sudo -S myModule.ko

Is there a way to avoid giving the password in plain text. Perhaps someway to give my user account permissions to do this?

Thanks.

---

### Post by SavageWolf on 2011-08-24
Why are you using pipes? If you are running it yourself you can just enter the password yourself. If you are using cron or the like, you can add it to root's crontab or the like...

---

### Post by ufuser01 on 2011-08-24
This module requires frequent loading and unloading and is handled by a python script. So, the above line is in a script which is called from python as a system command.

Any suggestions?
> **SavageWolf said:**
> Why are you using pipes? If you are running it yourself you can just enter the password yourself. If you are using cron or the like, you can add it to root's crontab or the like...

---

### Post by gizmo720 on 2011-08-24
When do you need the script called? Most times the system has a built in file that will execute as root.

---

### Post by ufuser01 on 2011-08-24
Thanks. What system file is that?
> **gizmo720 said:**
> When do you need the script called? Most times the system has a built in file that will execute as root.

---

### Post by wojox on 2011-08-24
```
sudo insmod --autoclean myModule.ko
```

Also you can add to /etc/modules: kernel modules to load at boot time.

---

### Post by ufuser01 on 2011-08-24
Thanks. I'll try that. But I don't need this on boot right now. I am still testing and for now, I need to be able to load and unload without a password.

Thanks.
> **wojox said:**
> ```
sudo insmod --autoclean myModule.ko
```Also you can add to /etc/modules: kernel modules to load at boot time.

---

### Post by ufuser01 on 2011-08-26
Figured it out: All I needed is to change the permission on insmod and rmmod to 4755

chmod 4755 /path/insmod

> **ufuser01 said:**
> Thanks. I'll try that. But I don't need this on boot right now. I am still testing and for now, I need to be able to load and unload without a password.

Thanks.

---

### Post by wojox on 2011-08-26
> **ufuser01 said:**
> Figured it out: All I needed is to change the permission on insmod and rmmod to 4755

chmod 4755 /path/insmod

Sorry. I missed the part where you said you are running it from a script. :P

---

