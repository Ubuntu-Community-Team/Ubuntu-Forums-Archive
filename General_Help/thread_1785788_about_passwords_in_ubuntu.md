---
title: "about passwords in ubuntu"
date: 2011-06-18
forum: General Help
---

### Post by Coolmariorocks on 2011-06-18
I want to know do i really to have a password in ubuntu? cause on my windows 7 pc i have no password at all. I hate having passwords on a computer.

---

### Post by cracker89 on 2011-06-18
Well, we'll really have to go back far for u to understand this. I suggest you read up a bit on what sudo is and what the root is. Apart from that, nope, where you do not *need* to have a password, i'd suggest u keep one. Its part of why Linux is so much more secure than windows. 
I like having no viruses and full control over a computer. :) Cheers.

---

### Post by amauk on 2011-06-18
You can fudge a completely passwordless system by using auto-login on the GUI and editing /etc/sudoers to not require a password for sudo

but this is akin to removing all the locks and catches from your windows and doors
You'll come home one day and find someone else living in your house

---

### Post by cracker89 on 2011-06-18
> **Coolmariorocks said:**
> I want to know do i really to have a password in ubuntu? cause on my windows 7 pc i have no password at all. I hate having passwords on a computer.

> **amauk said:**
> You can fudge a completely passwordless system by using auto-login on the GUI and editing /etc/sudoers to not require a password for sudo

but this is akin to removing all the locks and catches from your windows and doors
You'll come home one day and find someone else living in your house

Quite. Well put, Sir!

---

### Post by prodigy_ on 2011-06-18
> **amauk said:**
> You can fudge a completely passwordless system by using auto-login on the GUI and editing /etc/sudoers to not require a password for sudo
Only it won't be passwordless this way and may still ask for password occasionally. And you guys are flooding instead of helping. ;)

Anyway... In terminal window issue the following commands:
```
sudo sed -i -e 's/\(auth.*pam_unix.so.*nullok\).*/\1/g' /etc/pam.d/common-auth
sudo passwd -d $(whoami)
```
Bingo.

If you have more than one user account and you want all accounts to be passwordless, you'll need to use **passwd -d** command for every user.

---

### Post by dFlyer on 2011-06-18
> **Coolmariorocks said:**
> I want to know do i really to have a password in ubuntu? cause on my windows 7 pc i have no password at all. I hate having passwords on a computer.

Linux or Ubuntu in specific is not windows. The password for ubuntu is for your protection. If you want to boot without the password you can set ubuntu to skip the login screen and start ubuntu. I would not recommend deleting your password as that would still be needed by sudo to upgrade or install update and do maintenance on your system. It's also not good to bypass the login screen but a few or maybe more windows users do, as I can't understand why.

---

