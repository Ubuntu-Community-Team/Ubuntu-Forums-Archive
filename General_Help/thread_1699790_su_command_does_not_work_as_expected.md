---
title: "su command does not work as expected"
date: 2011-03-04
forum: General Help
---

### Post by natomb on 2011-03-04
Hello,


I have a number of machines running Ubuntu. On one machine I have the problem that the "su"-command does not work as expected.

When login as the local user "myroot", I can execute "sudo su -" and switch to root-user. Trying executing "su bjoern" (a valid user in an LDAP directory), I get the error message "setgid: Die Operation ist nicht erlaubt".

When login as the user "bjoern", I can login. When I try to execute "su myroot", I get the error message "su: Fehler bei Authentifizierung". I am quite sure that I have given the correct password.

As root, I can do both "su bjoern" and "su myroot" without problem.

What could be the problem?

```
which su
``` returns ```
/bin/su
``````
ls -Al /bin/su
``` returns ```
-rwsr-xr-x 1 root root 36864 2011-02-14 23:11 /bin/su
```

Thank you very much for your assistance.
  Bjoern

---

### Post by An Sanct on 2011-03-04
Here too, if I run just
```
su
```I get the password prompt, but it seems, that it wants the root password
when
```
sudo su
```It asks me explicitly for the password for my account, then I have root access.

PS.
```
man su
``` provides additional data.

---

### Post by An Sanct on 2011-03-04
Yes, that's a way to solve this ... I just don't think it is up to the security standards, Linux should stand for...

A normal user, that is also a sudoer, does not need to have root access, that's why "sudo su"

---

### Post by natomb on 2011-03-04
I agree with An Sanct. Of course, I could set a root-password that I know. But:

(1) it would not solve the problem, that I cannot "su bjoern" from myroot account (vice versa)

(2) it works on another machine

I would highly appreciate hints for further analysis to solve this problem.

---

### Post by MrEgg on 2011-03-04
Have you tried "sudo su bjoern" from myroot?

---

### Post by natomb on 2011-03-04
I have just tried

```
sudo su bjoern
```

from user myroot and could login. Fine, this could be a workaround for switching to other users from myroot-account.

Nevertheless, there is still the open point that I cannot su anywhere from bjoern-account on that machine. But this is the much more occasional thing to happen since I am usually working from my user account and not the myroot-account.

Thank you
  Bjoern

---

### Post by natomb on 2011-03-08
Searching further, I could find the following instruction which solved my problem.

[http://ubuntuforums.org/showthread.php?t=1509778](http://ubuntuforums.org/showthread.php?t=1509778)

Thank you.

---

### Post by psusi on 2011-03-08
1)  Don't use su.  If you want a root shell, use sudo -s.

2)  Don't set a root password.  It enables security holes and if you forget the password, you'll have trouble booting into rescue mode.

---

### Post by tgm4883 on 2011-03-08
> **psusi said:**
> 1)  Don't use su.  If you want a root shell, use sudo -s.

2)  Don't set a root password.  It enables security holes and if you forget the password, you'll have trouble booting into rescue mode.

Booting into rescue mode shouldn't have any issues if there is a root user password set. It boots into single user mode which shouldn't prompt for that information at all.

---

### Post by psusi on 2011-03-08
> **tgm4883 said:**
> Booting into rescue mode shouldn't have any issues if there is a root user password set. It boots into single user mode which shouldn't prompt for that information at all.

No, booting into rescue mode requires the root password, unless there isn't one.  The default Ubuntu install has no root password; the account is just locked so normal logins can't use it, but rescue mode bypasses the lock.  If you set a password, then you will be prompted for it when booting into rescue mode.

---

### Post by tgm4883 on 2011-03-08
> **psusi said:**
> No, booting into rescue mode requires the root password, unless there isn't one.  The default Ubuntu install has no root password; the account is just locked so normal logins can't use it, but rescue mode bypasses the lock.  If you set a password, then you will be prompted for it when booting into rescue mode.

Interesting, you learn something new every day

---

