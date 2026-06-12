---
title: "sudo and environment"
date: 2010-08-27
forum: General Help
---

### Post by quickk on 2010-08-27
Hi all, 

  I want to compile something, using sudo:

sudo make

the problem is that my environment is not preserved when the sudo command is invoked, and thus my compiler calling commands don't work.  I tried

sudo -E make

but this does not work either.  Any suggestions?  At the moment, all of my environment is set in the .profile file.  I would like this to be preserved when I invoke sudo.

Thanks!

---

### Post by LinuxHelper on 2010-08-27
Whenever i want to build something on a new computer I've always had to install 
build-essential

```
sudo apt-get install build-essential 
```

---

### Post by LinuxHelper on 2010-08-27
Whenever i want to build something on a new computer I've always had to install 
build-essential

```
sudo apt-get install build-essential 
```

Can you build other programs? Or is it just the environment that is not being preserved?

---

### Post by Vaphell on 2010-08-27
why do you want to compile a program with sudo in the first place? you don't need that to complile, only to install the result with 'make install'

---

### Post by quickk on 2010-08-27
> why do you want to compile a program with sudo in the first place? you don't need that to complile, only to install the result with 'make install'

Duh!  I didn't think of this.  Thank you for your help!

On a side note though, I would still like to know how to preserve the environment with the use of sudo.  As I understand it, Ubuntu does not have a "root" user, so I can't just copy my environment variables to the the root user's .bashrc or .profile.

---

### Post by sisco311 on 2010-08-27
> **quickk said:**
> 
On a side note though, I would still like to know how to preserve the environment with the use of sudo.  As I understand it, Ubuntu does not have a "root" user, so I can't just copy my environment variables to the the root user's .bashrc or .profile.

The root user password is locked by default, but root is a valid user.

Yo can start a root shell with **sudo -i**.

For details, check out:
```
man sudo
man sudoers

```

---

