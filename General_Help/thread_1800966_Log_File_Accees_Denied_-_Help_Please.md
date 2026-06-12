---
title: "Log File Accees Denied - Help Please"
date: 2011-07-09
forum: General Help
---

### Post by len_wynne on 2011-07-09
Today I ran fkhunter, and it created a log, but I cannot read it, as it says I am not the owner. I am running as an administrator so not sure what I need to do to change the permissions here. Any help would be appreciated.

Thanks

---

### Post by matt_symes on 2011-07-09
Hi

Navigate to the directory where the log file is installed and type

```
ls -l <log_filename>
```

That is a small L above. Change <log_filename> to the name of the log file.

Post back the results here. It may just be a case of adding you to the correct group but we will know when we see the permissions. 

That is a better solution than changing ownership of the file.

Kind regards

---

### Post by len_wynne on 2011-07-09
It shows this

-rw------- 1 root root 120264 2011-07-09 15:04 rkhunter.log

---

### Post by matt_symes on 2011-07-09
Hi

> **len_wynne said:**
> It shows this

-rw------- 1 root root 120264 2011-07-09 15:04 rkhunter.log

The file is owned by root and only the root user has read/write access to the file. The quickest way might be to change the owner or permissions of the file after all.

```
sudo chown <user_name>:<user_name> rkhunter.log
```

Replace <user_name> with your user name.

...or you can use... 

```
chmod 755 rkhunter.log
```

to change the permissions.

Enter your password. It will not be echoed to the screen.

You can also view it as root user if you so wish.

```
sudo less rkhunter.log
```

Kind regards

---

### Post by len_wynne on 2011-07-09
Thank you Matt!

---

### Post by 1clue on 2011-07-09
Why not, instead of invalidating the integrity of the file by changing ownership, simply use **sudo less rkhunter.log**?

---

### Post by matt_symes on 2011-07-09
Hi

> **1clue said:**
> Why not, instead of invalidating the integrity of the file by changing ownership, simply use **sudo less rkhunter.log**?

I gave him that option. Maybe you missed it in my post. Changing the ownership of that file is not a problem.

Kind regards

---

### Post by 1clue on 2011-07-09
Yeah, I saw the chmod and came unglued.  Sorry about that.

IMO changing that file's ownership is going to be a problem, if for no other reason that it will be marked as a tampered-with file on the next scan.

---

### Post by len_wynne on 2011-07-09
Yes that is the one I used. I am paranoid about doing anything that messes with root :D

---

