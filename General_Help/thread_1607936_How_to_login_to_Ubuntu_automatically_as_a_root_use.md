---
title: "How to login to Ubuntu automatically as a root user ?"
date: 2010-10-28
forum: General Help
---

### Post by Andy Chang on 2010-10-28
How to login to Ubuntu automatically as a root user ?
I'd like my system boot into text mode directly and login as root automatically without entering username/password, what should I do? My ubuntu version is 9.10.
I just change /etc/gdm/custom.conf file as follows
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=true
TimedLogin=root
AutomaticLogin=root
TimedLoginDelay=30
 
But the system still can't login automatically. 
Anybody any idea? 
Thanks.

---

### Post by ajgreeny on 2010-10-28
The root user in ubuntu is locked by default, so unless you have unlocked it yourself by carrying out the appropriate actions, you wil not be able to do what you want.

It is also forbidden to give instructions in this forum about how to unlock the root user account, so I think you will need to search elsewhere for the way in which you can do it.

Why do you need to do this, anyway?  There is almost nothing that you can not do with sudo, that can be done with the root user account, and anyone who really does need the root user account should know enough about linux to be able to do that already.

---

### Post by tgm4883 on 2010-10-28
> **ajgreeny said:**
> The root user in ubuntu is locked by default, so unless you have unlocked it yourself by carrying out the appropriate actions, you wil not be able to do this.

It is also forbidden to give instructions in this forum about how to unlock the root user account, so I think you will need to search elsewhere for the way in which you can do it.

Why do you need to do this, anyway?  There is almost nothing that you can not do with sudo, that can be done with the root user account, and anyone who does really need the root user account should know enough about linux to be able to do that already.

where is it forbidden, i've never seen that?

In any case, he wants to boot into single user mode to a command prompt. The OP edited a gdm conf file, which is graphical mode. He likely wants to research editing grub.

---

### Post by ivarn on 2010-10-28
Ok why would you do such a "stupid" and risky thing?
Also, have you enabled the root account yet?
```
sudo passwd root
```

---

### Post by endotherm on 2010-10-28
> **tgm4883 said:**
> where is it forbidden, i've never seen that?

In any case, he wants to boot into single user mode to a command prompt. The OP edited a gdm conf file, which is graphical mode. He likely wants to research editing grub.
sticky in the Security Discussions sub-forum. 

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by matt_symes on 2010-10-28
Hi  

Why do you want to login as root? Root is locked for a reason. What are you trying to do?

Kind regards

---

### Post by aysiu on 2010-10-28
Please read this:
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=1486138)

Thanks!

---

