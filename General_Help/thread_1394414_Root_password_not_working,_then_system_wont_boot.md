---
title: "Root password not working, then system wont boot"
date: 2010-01-30
forum: General Help
---

### Post by miiila on 2010-01-30
Hi everybody,

let me apollogize for possibility of bothering with solved problem, but I was not able to found solution.

I wanted to add new user in UBUNTU 9.10 via graphical enviroment. Ive opened User and Groups, logged as root, checked my normal account and with closing it, system freeze for some time. Then I close Users and Groups (by mistake). When I have opened it second time, it didnt accepted root password. Sudo didnt worked as well. I have restarted PC and since that I am not able to boot into UBUNTU. It cannot mount system disk (/dev/sda5) and it runs only maintain shell (or how it is called). dmesg | tail showed me about rows with error in initial scripts. Grub is working, but without configuration (time counting).

My lame idea is that it could be caused by suspended system to hard drive. I  have suspended it, but when I want to wake it up, it normally started (didnt continue). And with this problem, it only shows black and white UBUNTU logo like in waking of from suspend.

I am working on desktop dual boot, with windows xp. Ubuntu is on /dev/sda5, swap on /dev/sda6. No problems identified before this one.

I will attach errors messages and `dmesg | tail` since I get my nerves able to see it again :-)

Thanks in advance for any suggestion!
Best reg(t)ards

---

### Post by nothingspecial on 2010-01-30
Restart

press shift & escape

coose recovery > root shell

type ```
adduser username admin
```

exit

Then reboot

Change username for your actual username

---

### Post by miiila on 2010-01-30
no change - pressing shift escape didnt do anything, I was in maintanance shell again. Group admin doesnt exist, using group root printed error
gpasswd: Cannot lock /etc/group

It makes, sense because there is no / filesystem mounted :-) mountall reports unable to mount filesystem. Dmesg has only some login scripts (with no error).

EDIT: Problem is probably different - it writes "unable to mount /dev/pts". Any suggestion?

---

