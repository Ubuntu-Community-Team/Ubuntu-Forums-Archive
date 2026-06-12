---
title: "Let user install ONLY from software center"
date: 2010-07-17
forum: General Help
---

### Post by kapital on 2010-07-17
Is it possible to configure Ubuntu to allow a user to only install from the software center and not gain any other admin privileges?

I have enabled dpkg, apt-get and synaptic through visudo and I can install from there but the software center still prompts for my admin user's password. Just to be clear: it is not prompting me for the user's sudo password but for the password of the account that was created during installation.  

I basically want to let users install anything they like through the package managers but not do any other root stuff (like sudo rm -rf /).

---

### Post by yetiman64 on 2010-07-17
> **kapital said:**
> Is it possible to configure Ubuntu to allow a user to only install from the software center and not gain any other admin privileges?

I have enabled dpkg, apt-get and synaptic through visudo and I can install from there but the software center still prompts for my admin user's password. Just to be clear: it is not prompting me for the user's sudo password but for the password of the account that was created during installation.  

I basically want to let users install anything they like through the package managers but not do any other root stuff (like sudo rm -rf /).

As far as I understand, ANY installation of software to a system location, requires root access (sudo password) and cannot be done as normal user. 

Being able to install software would require a user to be in the sudoers file and would allow the use of any sudo commands, like your example above.

Software center prompts for the password and thus can only be used by someone with admin privileges (that is someone in the sudoers file).

Note, the original password entered on install is for all intents and purposes the root password in that the root account is disabled by default in Ubuntu - the use of "sudo" temporarily raises the user's privileges to that of root as needed.

---

### Post by kapital on 2010-07-17
thanks for your reply!

let me clarify. 

I have an account called "admin" and an account "guest". Only admin is part of the sudo group but I have set the following in the sudoers file:
```

guest ALL=(ALL) /usr/sbin/synaptic
guest ALL=(ALL) /usr/bin/apt-*
guest ALL=(ALL) /usr/bin/dpkg*
guest ALL=(ALL) /usr/bin/software-center

```

So the guest can install software through all these ways. The problem was that,as "guest" you could launch synaptic from the menu or invoke apt-get and dpkg through the commandline BUT the software-center prompts for "admin's" password when you want to install something. 

I worked around this issue by changing the software-center launcher to use the command:
```

gksu --description /usr/share/applications/ubuntu-software-center.desktop /usr/bin/software-center

```
rather than just ```

/usr/bin/software-center.

``` 
It now prompts for a password once when launched and that is all. 

It is a bit of a workaround but it is quite clean and fits in how synaptic behaves so I am happy with it.

---

