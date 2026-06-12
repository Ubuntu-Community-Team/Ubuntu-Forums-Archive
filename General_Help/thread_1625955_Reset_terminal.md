---
title: "Reset terminal"
date: 2010-11-19
forum: General Help
---

### Post by Ric_NYC on 2010-11-19
Everytime I start the Terminal I got this message:



mkdir: cannot create directory `/dev/cgroup/cpu/user/3271': No such file or directory
bash: /dev/cgroup/cpu/user/3271/tasks: No such file or directory


How to reset the Terminal so it starts the way it used to?



I started to get that message After I tried this:


mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent



sudo chmod +x /etc/rc.local



if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi



sudo gedit /usr/local/sbin/cgroup_clean


sudo chmod +x /usr/local/sbin/cgroup_clean

---

### Post by sisco311 on 2010-11-19
Search the bash init files for the mkdir command:
```
grep mkdir /etc/profile /etc/bash.bashrc ~/.bash_profile ~/.bashrc
```

Edit the file which contains it and delete the command.

---

### Post by Ric_NYC on 2010-11-19
> **sisco311 said:**
> Search the bash init files for the mkdir command:
```
grep mkdir /etc/profile /etc/bash.bashrc ~/.bash_profile ~/.bashrc
```

**Edit the file which contains it and delete the command**.

Thanks. That worked! Back to normal now!

---

