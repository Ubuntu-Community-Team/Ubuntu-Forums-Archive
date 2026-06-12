---
title: "software installation when root has different user name"
date: 2012-08-28
forum: General Help
---

### Post by neerajjain77 on 2012-08-28
Hello, 

In my work place, they setup computers such that the root has different user name. So the usual way of installing softwares using sudo does not accept the password. Nor does the graphical software installation. I have tried sudo -i , but it does not work. Can anybody suggest how to access root privileges and install software. One way is to logout from my normal user account and login to root account and install softwares. But this is not possible all the time. Is there a way to have root privileges both for graphical and command line installations without logging out. I am using ubuntu 12.04. 

Thanks for your help.

---

### Post by andrewc6l on 2012-08-30
I've never done it before, but you might want to look into the runaspw and runas_default options for /etc/sudoers.

You might also be able to just su rather than sudo.

---

### Post by dcstar on 2012-08-31
> **neerajjain77 said:**
> Hello, 

In my work place, they setup computers such that the root has different user name. So the usual way of installing softwares using sudo does not accept the password. Nor does the graphical software installation. I have tried sudo -i , but it does not work. Can anybody suggest how to access root privileges and install software. One way is to logout from my normal user account and login to root account and install softwares. But this is not possible all the time. Is there a way to have root privileges both for graphical and command line installations without logging out. I am using ubuntu 12.04. 


[LIST=1]
[*]I have *never* seen a Unix/Linux installation where root has been renamed.
[*]If you have not been given the account that has Admin privileges, then the people who built and administer those machines probably have a very good reason for it.
[/LIST]

---

### Post by andrewc6l on 2012-08-31
Sometimes root got renamed on Internet-facing Unix boxes to reduce the probability of a successful attack. (This used to be done more than it is now - nowadays you just reject root logins that come from the network.)

Regardless, if you don't have root access at work and you need it, you should ask someone rather than try to get it via Linux hacks :-)

---

### Post by dcstar on 2012-08-31
> **andrewc6l said:**
> Sometimes root got renamed on Internet-facing Unix boxes to reduce the probability of a successful attack. (This used to be done more than it is now - nowadays you just reject root logins that come from the network.)
.........

Or you do what Ubuntu and other distros do, disable logins on root and require people to use sudo. That satisfies all security requirements including people looking to con a hack method out of Internet forums.

---

### Post by mcduck on 2012-09-01
> **neerajjain77 said:**
> Hello, 

In my work place, they setup computers such that the root has different user name. So the usual way of installing softwares using sudo does not accept the password. Nor does the graphical software installation. I have tried sudo -i , but it does not work. Can anybody suggest how to access root privileges and install software. One way is to logout from my normal user account and login to root account and install softwares. But this is not possible all the time. Is there a way to have root privileges both for graphical and command line installations without logging out. I am using ubuntu 12.04. 

Thanks for your help.

Use "su" instead of "sudo", or ask the admins to add your user into sudoer's file so that you can use sudo to gain root privileges.

Of course if the admins haven't given you such privileges, and are not willing to do that, there's nothing you can do. And as always, actually logging in to desktopa s root would be a bad idea, you should only use such privileges for the programs/tools that need them, not for the whole desktop...

---

