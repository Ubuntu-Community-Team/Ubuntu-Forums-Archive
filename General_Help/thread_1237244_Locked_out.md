---
title: "Locked out"
date: 2009-08-11
forum: General Help
---

### Post by christym on 2009-08-11
To keep the kids from messing with configuration files, I activated the root user, thinking I would be able to log on as root from time to time to perform configurations. 

Using -su I can log on as root in a terminal, however I can't access many of the menu tasks as the root user because root is not permitted to log on at the splash screen. 

How can I change this to enable the root user to operate the menu system?
Thanks
Christym

---

### Post by Wim Sturkenboom on 2009-08-11
I think you have choosen the wrong approach. Each kid should have it's own username/password and no permission to modify the system.

To answer the question: I don't have Ubuntu at hand, but look for gdm.conf (if I'm not mistaken). There should be something like 'allowroot'.

---

### Post by TuckLive on 2009-08-11
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by arch0njw on 2009-08-11
> **Wim Sturkenboom said:**
> I think you have choosen the wrong approach. Each kid should have it's own username/password and no permission to modify the system.


I am going to second this.

Doing things strictly as root is risky because root is the ultimate user.  The better approach here is for each kid to have their own login OR a single shared login, and then for you to have your own login.  From any user you can use the "sudo" command or from the run dialog use "gksudo".  Technically, you don't need another account to do this if all you want to do is sys admin stuff -- but it could be handy if there is one way you want to setup the desktop for the children to use, and another for you to do sys admin tasks.

Another advantage to having one or more accounts for the children is that you can look up how to modify the sudoers list -- that's the list of users who are permitted to use the "sudo" command.  You can then specifically exclude their account/s and ensure that only *your *sys admin account has the rights to make system changes.

---

### Post by christym on 2009-08-11
Thanks for all these suggestions
Christym

---

