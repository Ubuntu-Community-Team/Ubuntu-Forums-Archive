---
title: "/etc/sudoers file permissions changed"
date: 2011-03-18
forum: General Help
---

### Post by falconer-bob on 2011-03-18
I can no longer use sudo for anything.  It says the /etc/sudoers has 640 permissions should be 440.  Of course you can't change permission delete the file or anything because you don't have permission and you can't be sudo.  Since I am the only one that does anything to the system other than software (?) how would this get changed?  How do I fix it?  This sure isn't falconry!:confused:

---

### Post by lithopsian on 2011-03-18
You might be able to login as root, or you can change it using a Live CD.

---

### Post by sisco311 on 2011-03-18
Boot into *Recovery Mode* and change the permissions back to 0440:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT:

You don't even have to boot in recovery mode, just open a terminal and run:
```
pkexec chmod 0440 /etc/sudoers
```

---

### Post by burton247 on 2011-03-18
Recovery would work, but can you not just su to root? Then do it from there?

---

### Post by sisco311 on 2011-03-18
> **burton247 said:**
> Recovery would work, but can you not just su to root? Then do it from there?

By default, in Ubuntu the root account password is locked, but yes if the OP enabled the root account, he can login as root or su to root and fix the permissions of file.

policykit-1 provides a setuid root application: pkexec which allows an authorized user (by default, in Ubuntu, user from the admin group) to execute PROGRAM as another user.

---

### Post by burton247 on 2011-03-18
Oh right, my bad. Cheers for setting me straight :)

I must have enabled mine a long time ago lol

---

### Post by falconer-bob on 2011-03-18
> **sisco311 said:**
> Boot into *Recovery Mode* and change the permissions back to 0440:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

EDIT:

You don't even have to boot in recovery mode, just open a terminal and run:
```
pkexec chmod 0440 /etc/sudoers
```


Worked just fine (pkexec)  Thanks for your help everyone!  There was no way that I could get to the sudo account so pkexec worked!

---

### Post by sisco311 on 2011-03-18
> **burton247 said:**
> Oh right, my bad. Cheers for setting me straight :)

I must have enabled mine a long time ago lol

No problem. :)

> **falconer-bob said:**
> Worked just fine (pkexec)  Thanks for your help everyone!  There was no way that I could get to the sudo account so pkexec worked!

Cool! You're welcome!

Don't forget to mark this thread as [SOLVED]. Thanks!

---

