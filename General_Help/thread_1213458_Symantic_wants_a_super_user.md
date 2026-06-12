---
title: "Symantic wants a super user???"
date: 2009-07-14
forum: General Help
---

### Post by edhawk2 on 2009-07-14
Running 8.04 Ubuntu, I'm the only user on a Dell laptop, when I try to bring up Symantic takes my password then gives an error message:

E: 'dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem'
E: _cache ->open() failed, please report.

when I run the command in terminal, it says I need super user priviledge

I thought on a single user system I was the super user. I've recently run Synaptic without this problem.

Any help??

---

### Post by Wiebelhaus on 2009-07-14
Use:

```
sudo dpkg --configure -a
```

Enter your pass.

"sudo" is short for "Super User Do"

---

### Post by Gatemaze on 2009-07-14
run
sudo dpkg --configure -a

and nope you are not the superuser, you are a system user though which is close enough as it allows you to run sudo. the superuser account is called root. so if you want to run any kind of superuser stuff, prefix a sudo in the beginning.

---

