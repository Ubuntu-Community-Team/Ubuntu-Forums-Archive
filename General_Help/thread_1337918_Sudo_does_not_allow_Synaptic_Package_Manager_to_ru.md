---
title: "Sudo does not allow Synaptic Package Manager to run?"
date: 2009-11-25
forum: General Help
---

### Post by Logank9 on 2009-11-25
I am trying to set up synaptic package manager so I enter my root password to run it, but it asks for my user password instead, which isn't allowed to admin privileges. Resulting in the error message "Sudo does not allow this application to run. Please contact your network administrator". How would I go about setting it up so I enter my root password instead?

---

### Post by louieb on 2009-11-26
Sounds like you changed the Ubuntu security model by 1. Giving the root account a password and 2. removed yourself from the admin group or deleted the admin user. Is that correct?

1st I would restore admin rights to your user id or create a user with admin rights.
Since I don't know how you lost admin rights - [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo) 

2nd I would disable the root account ```
sudo usermod -p '!' root
```

More here [RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo") 
[forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by Logank9 on 2009-11-26
I didn't lose admin rights it's just that I don't want to give my main account them. Synaptic Package Manager asks for the password of the account I'm logged in as. This is a problem because the current account does not have admin rights. How do I set it up so that I have to type in the root password instead. This is only a problem with Synaptic Package Manager. Everything else works fine.

---

### Post by akakingess on 2009-11-26
> **Logank9 said:**
> I didn't lose admin rights it's just that I don't want to give my main account them. Synaptic Package Manager asks for the password of the account I'm logged in as. This is a problem because the current account does not have admin rights. How do I set it up so that I have to type in the root password instead. This is only a problem with Synaptic Package Manager. Everything else works fine.

Does this also happen if you try to use the "Ubutu Software Center" from the main "Applicaions" menu. I know you need to get into the Package Manager, but just to troubleshoot, it would be interesting to note if it affected both areas.  However, I do agree that you should login as someone with admin/root privileges in order to do administrative stuff like the Synaptic Package Manager.

Or even the Update Manager for that matter...Basically, I am just wondering if it is only affecting the Package Manager...

Also, as an alternative, could you create an account that you only log in as just to do such administrative maintenance/installs/upgrades?

---

### Post by Logank9 on 2009-11-26
I didn't notice before, but it's on everything. It never asks for the root password.

---

### Post by akakingess on 2009-11-26
I would definitely create an account specifically for doing adminstrative stuff. It by no means has to be the main account, you just have to add it to the admin and root groups and that should be enough, and then when you need to update/install something just go on up and choose "switch user" and temporarily log in as the admin empowered user, do what needs to be done and switch back over. That would be the way I would handle it if say the main account were set up for my 5 year old (which it is on one of our 6 machines). Maybe an annoying step, but I believe it to be a necessary one. Good luck to you as it is way past my bedtime, I hear the wife calling :)

---

### Post by kerry_s on 2009-11-26
run-> gksu-properties
change it to gksu

---

### Post by louieb on 2009-11-26
> **Logank9 said:**
> I didn't notice before, but it's on everything. It never asks for the root password.

If it opens and works with your user password that the way Ubuntu is designed to work.  [akakingess]("http://ubuntuforums.org/member.php?u=814426") in post #6 describes the best alternative. 

Once you open a program as administrator, for a period of time (about 15 minutes) if you open another program as administrator, it won't ask again. 

> **kerry_s said:**
> run-> gksu-properties - change it to gksu

:confused:Wondered what that does. so I tried it - gksu was not an option. only sudo and su - Hardy is installed.  no man page either.

---

### Post by Logank9 on 2009-11-26
After little tinkering I found that setting gksu-properties as "su" and "force enable" fixes everything.

**Edit:**

Those settings fix a few things anyways. Most things still ask for the user password to perform administrative tasks.

---

