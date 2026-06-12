---
title: "High disk usage"
date: 2009-07-17
forum: General Help
---

### Post by t12121 on 2009-07-17
I just noticed that I only have like 32 GB free on my ubuntu 8.04 machine.  I did a Disk usage analyzer and I have 4 large files of 118+ GB each.  What are these files: pl.UTF-8 (118.8 GB), man(118.8 GB), cache(119.0 GB), and var(119.3 GB). Are these all one file? Can I get rid of them? If so how do I get rid of them?
Any assistance is thanked

Tom

---

### Post by drs305 on 2009-07-17
A few of those sound like folders and not files. You can run the following command to find the actual file names if this is the case:
```
sudo find / -name '*' -size +1G  

```

You can open a browser with root privileges. Use SHIFT-DEL to remove the files you find. Be careful, as SHIFT-DEL permanently removes the files and as root you can delete *anything* on your system.
```
gksudo nautilus
```

There is a wiki link in my signature line (Disk Space) that explains common reasons for 'lost' disk space, and how to find and recover it.

---

### Post by t12121 on 2009-07-17
find: /proc/5992/task/5992/fd/6: No such file or directory
find: /proc/5992/task/5992/fdinfo/6: No such file or directory
find: /proc/5992/fd/6: No such file or directory
find: /proc/5992/fdinfo/6: No such file or directory
/var/log/messages.3.gz
/var/cache/man/pl.UTF-8/6125
/var/cache/man/pl.UTF-8/index.db
/var/cache/man/pl.UTF-8/6078
find: /home/jerry/.gvfs: Permission denied

This is what is said but I have no idea what is means

---

### Post by Sidewinder1 on 2009-07-17
With all due respect, are you sure you're not misreading GB for MB? My entire drive with all of Ubuntu and my home (with some music and videos) only take up about 28.3 _G_B. On a side note, I believe the *MAN*, to which you refer is the MANual pages for terminal commands; open a terminal and type ```
man man
```  Don't think you's want to delete that.  :-)

HTH, 
Side

---

### Post by t12121 on 2009-07-17
> **Sidewinder1 said:**
> With all due respect, are you sure you're not misreading GB for MB? My entire drive with all of Ubuntu and my home (with some music and videos) only take up about 28.3 _G_B. On a side note, I believe the *MAN*, to which you refer is the MANual pages for terminal commands; open a terminal and type ```
man man
```  Don't think you's want to delete that.  :-)

HTH, 
Side

Nope its using 118+ GB

---

### Post by nikhilk on 2009-07-17
> **t12121 said:**
> find: /proc/5992/task/5992/fd/6: No such file or directory
find: /proc/5992/task/5992/fdinfo/6: No such file or directory
find: /proc/5992/fd/6: No such file or directory
find: /proc/5992/fdinfo/6: No such file or directory
/var/log/messages.3.gz
/var/cache/man/pl.UTF-8/6125
/var/cache/man/pl.UTF-8/index.db
/var/cache/man/pl.UTF-8/6078
find: /home/jerry/.gvfs: Permission denied

This is what is said but I have no idea what is means

You have got a list of files whose size is greater than 1GB. There are some spurious results but following are the "heavy-weights"
```
/var/log/messages.3.gz
/var/cache/man/pl.UTF-8/6125
/var/cache/man/pl.UTF-8/index.db
/var/cache/man/pl.UTF-8/6078
```

See if the condition is ameliorated after running```
sudo apt-get clean
```

---

### Post by t12121 on 2009-07-17
> **nikhilk said:**
> You have got a list of files whose size is greater than 1GB. There are some spurious results but following are the "heavy-weights"
```
/var/log/messages.3.gz
/var/cache/man/pl.UTF-8/6125
/var/cache/man/pl.UTF-8/index.db
/var/cache/man/pl.UTF-8/6078
```

See if the condition is ameliorated after running```
sudo apt-get clean
```

ok now that I know of the "heavy hitters" is it safe to delete those files?

---

### Post by Sidewinder1 on 2009-07-17
I wouldn't delete **anything** unless you're Absolutely Certain that you know exactly what it is; especially if they're located in root...
If you do, make certain you have backed-up your important data; I smell a reinstall... :-)

---

### Post by t12121 on 2009-07-17
> **Sidewinder1 said:**
> I wouldn't delete **anything** unless you're Absolutely Certain that you know exactly what it is; especially if they're located in root...
If you do, make certain you have backed-up your important data; I smell a reinstall... :-)

I deleted the file I have rebooted already seems to be working fine.  

Thanks for the help all!

---

### Post by drs305 on 2009-07-17
Too late. Was going to suggest moving them, then deleting if there were no problems.

---

