---
title: "Can't SSH as root"
date: 2009-11-23
forum: General Help
---

### Post by The Jinx on 2009-11-23
As the title suggests i can't get ssh to work as root. whenever i type "su" in terminal and it prompts me to enter my password I get "su: Authentication failure" but when I enter sudo and my password I don't have any problems. Can anyone please help. 

In addition, can you clarify the difference between su and sudo.

Thanks,
Jinx

---

### Post by undecim on 2009-11-23
Logging in as root is a bad idea, and root logins are disabled by default, because its very easy even for experienced users to mess up their system (not to mention the security issues involved.)

The rule of thumb is this: If you don't understand users, groups, and security well enough to know how to log in as root, you shouldn't be logging in as root.

You should just SSH with your normal username and use sudo for all your commands that need root privileges.

The main difference between the su and sudo commands is how they allow you to run commands as another user

su is an acronym for "switch user" and it will run another user's shell (usually bash) as that user. The default user is root, so "su" is basically the same as "su root". Also, su requires that you type the password of the user you want to switch to.

sudo, on the other hand, will run a single command as another user, and requires your password. It also checks the /etc/sudoers file to make sure that you are allowed to run that command as that user.

---

### Post by The Jinx on 2009-11-24
well I would at least like to know how to login as root for future references

---

### Post by JBAlaska on 2009-11-24
I believe it's against these forums ethics to give that info...But there is always Google.

Seriously, Just don't run as root especially in a remote session. [COLOR="Blue"]Edit: (Especially since undecim gave you the answer lol)[/COLOR]

---

### Post by defleopard98 on 2009-11-24
There is really no need to login as root at all, and if you **really** need to have a root shell, just run:
```
sudo -i
```
and enter your password. It is preferred to do that than have to root able to login in.

---

