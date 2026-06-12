---
title: "Emesene &quot;I refuse to run as a root&quot;"
date: 2010-12-23
forum: General Help
---

### Post by Ramy89 on 2010-12-23
Hello,I have my root account in ubuntu 10.10 maverick meerkat,I use it for everything.
Now when I try to run emesene it gives this windows:
```

root@ramy-Aspire-5745G:~# emesene
** Message: pygobject_register_sinkfunc is deprecated (GstObject)
I refuse to run as root. If you know the risks and still want to do it, just add the --i-know-that-running-emesene-as-root-is-bad option.
root@ramy-Aspire-5745G:~# 


```
It gives me the option to run it however,but I wish to know what are risks of running it with a root account.

---

### Post by Wtower on 2010-12-23
Duplicate thread:
[http://ubuntuforums.org/showthread.php?t=803011](http://ubuntuforums.org/showthread.php?t=803011)

Please first search through!

---

### Post by 98cwitr on 2010-12-23
logging in as root is, in general, not a smart way to operate. Use sudo

---

### Post by MSPdwalt on 2010-12-23
A trick I use when I know I'm going to have a lot to do as root is:
```
sudo su -
```

This will give you a root shell and you only have to enter your password once.

---

### Post by Wtower on 2010-12-23
Guys I don't think that anybody would need to run an instant messaging application as root

---

### Post by Ramy89 on 2010-12-23
The reason is that I would avoid to reput the password more times,I'll try that comand.
Anyone knows the reason why isn't smart to operate logging as a root?

---

### Post by fiddler616 on 2010-12-23
> **Ramy89 said:**
> The reason is that I would avoid to reput the password more times,I'll try that comand.
Anyone knows the reason why isn't smart to operate logging as a root?

Because it gives you--and everything you're running, whether you meant to run it or not--gratuitous amounts of power. This is part of the reason that Ubuntu (and Unix in general) is so secure--everything that's running has *just* enough power to do what it needs to do, and can't screw up the rest of your system.

---

### Post by Spyderkid on 2010-12-23
it can give unwanted applications/processes absolute power over the computer (and hackers)

it's not a good idea basicly.

---

### Post by Ramy89 on 2010-12-23
Ok so now I have the root account with all the data saved,how do I change privileges?

---

### Post by Wtower on 2010-12-23
You wouldn't change priviledges to root. You'd better create a new user with adduser:

[https://help.ubuntu.com/community/AddUsersHowto](https://help.ubuntu.com/community/AddUsersHowto)

Don't forget to add the new user to group admin. Take a loot at:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Finally, it is also a good practice to disable root login via ssh. In my personal experience, the vast majority of breakin attempts in my servers are for the root user on ssh. Do that ONLY after you are certain that the new user can issue a sudo command. This option is the PermitRootLogin option of the /etc/ssh/sshd_config file.

---

