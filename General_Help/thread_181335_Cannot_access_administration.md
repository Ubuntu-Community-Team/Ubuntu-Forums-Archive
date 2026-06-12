---
title: "Cannot access administration"
date: 2006-05-24
forum: General Help
---

### Post by wekion on 2006-05-24
i simply cannot access any of the administration items under the system menu ever since i just installed ubuntu. it prompts me for a password when i start one, after i key in my root password, it displays (for example) the "Starting Users and Groups" window icon on the taskbar, then it disappears after a few seconds... :confused:

i don't think my password is wrong because if i key in a wrong one, it just prompts me that my password is wrong...

i am running 5.10.

---

### Post by professor_chaos on 2006-05-24
Does the same thing happen when you type 

```
sudo users-admin
```

---

### Post by Phlosten on 2006-05-24
Your admin password is the same as the password which you use to log into your normal account.
Have you by any chance created a root account?
Ubuntu by default does not use a root account, but uses 'sudo' instead. If you have created a root account that could probably cause there issues.

---

### Post by wekion on 2006-05-24
this is what happens

```
myname@ubuntu:~$ sudo users-admin
Password:
myname@ubuntu:~$ sudo users-admin
myname is not in the sudoers file.  This incident will be reported.
myname@ubuntu:~$ sudo users-admin
myname@ubuntu:~$ sudo users-admin
```

after i key in my password the first time, nothing happens... then it threatens me, then it does nothing...

---

### Post by wekion on 2006-05-24
i don't think i explicitly created a root account

but i can "su" in the terminal, so probably there is one.

so how do i get rid of it?

---

### Post by professor_chaos on 2006-05-24
like Phlosten said, your sudo password by default is the same as the installer's password (ie samuel). Do you remeber changing roots password?
I dont know how to fix this off the top of my head, I will look around and post if I find anything.

You can try adding "samuel" to the admin group to try and gain sudo access back. From the terminal do this.
su
users-admin

---

### Post by wekion on 2006-05-24
thanks for the tip...

i actually thought that my username wasn't in the sudoers file, so i did a visudo, sure enough only root was there, not my username. so i added it and viola! everything works now...

thanks professor, it's people like you that make me foresee a long relationship with ubuntu...

---

### Post by wekion on 2006-05-24
to add on, this problem came about even though i practically didn't do any configuration at all after installation. so i'm not sure why i couldn't sudo with the account created during installation.

maybe the folks at ubuntu can take note of this?

---

