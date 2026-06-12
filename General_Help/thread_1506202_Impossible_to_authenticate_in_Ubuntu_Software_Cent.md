---
title: "Impossible to authenticate in Ubuntu Software Center"
date: 2010-06-10
forum: General Help
---

### Post by semsaudade on 2010-06-10
Hi to everybody. I apologize first because I do not know if this is the right section for my problem, but I could not find anything more suitable. 

I have an Asus 900 with Ubuntu Netbook Remix 10:04 In a nutshell: I realized today, trying to install a new program with Ubuntu Software Center, that I can not anymore authenticate myself as root. Of course I have not changed the password, but the old one is not anymore accepted ("Authentication failed"). 

The interesting thing is that I can install programs without problems (using the same old password) with the package manager in Administrative Tools (synaptic). Here, the authentication works well.


Opening a terminal, I can use sudo to run any command by providing my password, with no problem at all. Following some guides found on the web, I reset the root password (supplying the same one as before) and everything went well. Only .... nothing has changed! Ubuntu center software authentication always fails.

What could have happened? Maybe I did some mistake  by editing /etc/sudoers to solve another problem some days ago. Ubuntu told me that my username was not in the sudoers file, so I resolved it by adding to /etc/sudoers the line 
myusername ALL = (ALL) ALL 

I checked the contents of the file and, apart from this line added, it is as it was before (I compared with that on another PC with Ubuntu). 

Can anyone make some sense out of it? Starting from the fact that the package manager does function ... but software center does not... I am puzzled!

Thanks in advance for your patience and kindness!

---

### Post by dino99 on 2010-06-10
two ways:

- sudo dpkg-reconfigure software-center

or with synaptic

- right-click on package to remove/purge software-center, then reinstall it (and the meta-package too as it has been removed)

---

### Post by semsaudade on 2010-06-10
Thanks to Dino99 for his kind answer. I tried with sudo dpkg-reconfigure software-center, but with no result.

I believe it is not a problem specific of Ubuntu Software Center, but it is more related to authentication in general. Why did I need to add my username to sudoers file in order to use sudo comand? Such authentication was automatically granted to my username before and I never had necessity of changing sudoers file. So I think that something went wrong somewhere in Ubuntu authentication system. Any other idea?

Thanks a lot again!

---

### Post by sisco311 on 2010-06-10
Add your user to the admin group:
```
sudo gpasswd -a **username** admin
``` 

By default sudo is configured to allow users from the admin group to run commands as another user or root. This is the relevant line from the sudoers file:
```
...
%admin	ALL=(ALL) ALL
...

```

Some GUI application like Software Center, Users and Groups, Network Manager... use PolicyKit instead of sudo/gksu. Policykit, by default, just like sudo, is configured to allow users from the admin group to escalate their privileges.

---

### Post by semsaudade on 2010-06-11
Solved! The solution was resetting root's password, booting in recovery  mode. I simply re-entered my previous superuser password, which was (I  don't know why and how) deleted. Now everything is ok.

Thank you very much for helping!

---

