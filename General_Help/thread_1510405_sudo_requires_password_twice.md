---
title: "sudo requires password twice"
date: 2010-06-15
forum: General Help
---

### Post by rsteinmetz70112 on 2010-06-15
I recently upgraded one of my machines and now sudo requires me to enter the password twice, before executing the command.

su no longer works but I can log in as root.

Update Manager prompts for the password but then fails to download the the updates or upgrade the system.

I can "sudo apt-get update [or upgrade]". and it works, after I enter the password twice.

shh login does not work, it keeps asking for the password.

---

### Post by arrange on 2010-06-15
Could you post the contents of */etc/pam.d* somewhere? For example ```
tar czf /tmp/pam.tgz /etc/pam.d
```will pack the directory into a */tmp/pam.tgz* file which you can upload.

---

### Post by rsteinmetz70112 on 2010-06-16
Unfortunately I am now off site for several days and since ssh doesn't work I have no access to the computer.

I suspect the problem is modifications I made to pam.d to get winbind to work. Then when I upgraded from 8.10 -> 9.04 there were conflicts introduced.

I'm thinking about upgrading again to 9.10 and again 10.04, then tackling the problem since I understand that winbind has been a pam configuration in that release.

---

