---
title: "Best way to backup and restore apps and settings"
date: 2011-03-11
forum: General Help
---

### Post by TimEnid on 2011-03-11
i will be swapping my internal hd soon and installing ubuntu 10.10 on it. Then i want to put back all the apps that im currently using. Whats the best method to do this? I dont want to clone/backup my entire OS. I just want a method that will allow me to backup the apps, and then restore them on a clean ubuntu OS. Any suggestions?

---

### Post by Krytarik on 2011-03-11
You can make a list of currently installed packages, for installation after the initial setup, by following this guide:
[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

To retain all the settings of your user profile, you may backup "/home/USERNAME", and restore it after the setup, but I would just rename the initial home directory of your new user (instead of deleting it), just to be sure. And there may also arise some difficulties with one or another app after simply restoring the entire home directory.

---

### Post by TimEnid on 2011-03-11
thanks for the suggestion, but when i type in
 ```
$ dpkg --get-selections > /backup/installed-software.log
```

i get 
```
bash: /backup/installed-software.log: No such file or directory
```

---

### Post by Telengard C64 on 2011-03-11
> **TimEnid said:**
> ```
bash: /backup/installed-software.log: No such file or directory
```

Does the directory **/backup** exist? If not then you will need to create it first. You will probably also need root permissions (sudo) to write in the root directory of your system.

---

### Post by TimEnid on 2011-03-11
> **Telengard C64 said:**
> Does the directory **/backup** exist? If not then you will need to create it first. You will probably also need root permissions (sudo) to write in the root directory of your system.

now i get this
```
tim@tim-desktop:~$ sudo mkdir /backup
mkdir: cannot create directory `/backup': File exists
tim@tim-desktop:~$ dpkg --get-selections > /backup/installed-software.log
bash: /backup/installed-software.log: Permission denied
tim@tim-desktop:~$ sudo dpkg --get-selections > /backup/installed-software.log
bash: /backup/installed-software.log: Permission denied

```

---

### Post by Krytarik on 2011-03-12
Then simply choose another location where your user is permitted to write, I don't find a perfect way right now to pipe the output with sudo.
```
dpkg --get-selections > /home/USERNAME/installed-software.log
```

---

### Post by Telengard C64 on 2011-03-12
> **Krytarik said:**
> I don't find a perfect way right now to pipe the output with sudo.

I think the problem is that pipes and redirections are handled by Bash, which is running with user permissions and not root. Maybe something like this would work?

```
sudo sh -c 'dpkg --get-selections > /backup/installed-software.log'
```

---

### Post by Krytarik on 2011-03-12
> **Telengard C64 said:**
> I think the problem is that pipes and redirections are handled by Bash, which is running with user permissions and not root. Maybe something like this would work?

```
sudo sh -c 'dpkg --get-selections > /backup/installed-software.log'
```
Thanks, that works! Of course, I didn't run it with those very command but with "ls" instead, but that doesn't matter.

---

