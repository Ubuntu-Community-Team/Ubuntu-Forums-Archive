---
title: "possible problem with Terminal"
date: 2011-05-03
forum: General Help
---

### Post by hunterkasy on 2011-05-03
Just did a clean install to 11.04 64.  


when I open up Terminal the top 2 lines say this:

bash: /dev/cgroup/cpu/user/16891/tasks: No such file or directory
bash: /dev/cgroup/cpu/user/16891/notify_on_release: No such file or directory
user1@user1-Satellite-L305:~$ 

but I am able to use the terminal with no problems.  I am wondering if it is going to be a problem or not, and how to fix it

thanks

---

### Post by oldos2er on 2011-05-03
Look in your .bashrc file; you can comment out or delete the lines beginning with "/dev/cgroup/cpu...."

---

### Post by hunterkasy on 2011-05-03
> **oldos2er said:**
> Look in your .bashrc file; you can comment out or delete the lines beginning with "/dev/cgroup/cpu...."

I hate to say it but I need to know how and where the .bashrc file is  sorry

---

### Post by idoitprone on 2011-05-03
it a hidden file in your home directory

cd to go to home
ls -la to find the file
```
cd
ls -la
```

---

### Post by hunterkasy on 2011-05-03
> **idoitprone said:**
> it a hidden file in your home directory

cd to go to home
ls -la to find the file
```
cd
ls -la
```

thanks it fixed it.

---

### Post by oldos2er on 2011-05-04
The "." in front of the filename indicates it's a hidden file, which are sometimes referred to as dot files. Your home folder is full of them.

---

