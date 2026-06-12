---
title: "Just installed 10.4 again, no privelages!"
date: 2010-08-19
forum: General Help
---

### Post by jinba.ittai on 2010-08-19
Ive just installed 10.04 again and for some reason i have no write privelages. On all system files like the ETC folder or hidden files in the home folder are all read only. I know how to login to root by terminal and have all privileges but it would benefit more if i knew how to change this user account to have some privileges.

Help?

---

### Post by silbak04 on 2010-08-19
as long as you run "sudo" before whatever you're trying to do...you should have write privileges ..what exactly are you trying to edit, that's not working?

example ```
$ sudo nano /etc/ssh/sshd_config 
Password:
```

^ after entering that password, you should be able to edit that file if that's the file you wanted to edit, for example...if that really doesn't work, then I'll keep on thinking for a new solution.

---

### Post by jinba.ittai on 2010-08-21
I know i have to have "sudo" when using the terminal, but in the GUI i used to be able to view certain folders with system / hidden files and have read/write privileges. 

For example, my conky file, i used to be able to goto the home folder and edit it when ever i wanted, now i MUST sudo getid do edit anything. 

Kinda weird

---

