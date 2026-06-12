---
title: "sudo: setuid must be root"
date: 2010-04-09
forum: General Help
---

### Post by mayapower on 2010-04-09
Environment:
VirtualBox 3.1.6 for Windows hosts x86/amd64
Host: xp
Guest: kubuntu karmic 9.10

I was fiddling with some files and chmod command and suddenly something went wrong. I was getting this message:

```

sudo: setuid must be root

```
I am new to linux as well as virtualbox. I restarted the virtualbox and then kubuntu. I can reach upto the login screen and after entering the password, everything goes off and I can see terminal(bash).

Any idea what's wrong here and how do I solve this?

I tried couple of things but nothing worked.
Like the one here:
[http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html](http://mihirknows.blogspot.com/2008/06/sudo-must-be-setuid-root-solved-in.html)

Problem still persists and after entering password to login/welcome screen it switched to terminal asking for user name and password.

I also did a small change in sudoers.tmp as mentioned here:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Previously the line was like this:
```

Defaults env_reset

```I didn't change anything else 

What the hell is going on.......

Prashant

---

### Post by cjhabs on 2010-04-09
The ownership of /usr/bin/sudo should be:
-rwsr-xr-x 2 root root 143736 2010-02-25 18:27 /usr/bin/sudo

Note that root is the owner and that the owner has the "s" property set (setuid).
The permissions need to be 4755 (using chmod) and the owner needs to be root.

Whether you can do that or not with the current state of sudo you'll have to see - it sounds to me like the owner is incorrect.

---

