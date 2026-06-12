---
title: "subversion gnome keyring"
date: 2009-12-07
forum: General Help
---

### Post by karthik085 on 2009-12-07
Hi,
I would like to make subversion store passwords encrypted using gnome keyring and not ask for passwords every time I contact svn repository. Here are my current configuration:

In ~/.subversion/servers
[global]
store-passwords = yes
store-plaintext-passwords = no

In ~/.subversion/config
[auth]
store-passwords = yes
store-auth-creds = yes
password-stores = gnome-keyring , kwallet

After making this settings, I deleted ~/.subversion/auth and tried to connect to SVN, it didn't seem to store the password in gnome keyring and kept asking me for password every time I tried to connect to SVN. Any ideas on what seems to be a problem.

If SVN needs to be compiled with gnome keyring support, how can I do it without compiling it from source myself? Can I just install / re-install from ubuntu repository with the support?

Thanks,
K

---

### Post by wall0645 on 2010-08-03
Just bumping this. I am having the same problem.

To my knowledge, you only need to add the --with-gnome-keyring when compiling from source. It shouldn't be necessary when using the subversion that comes with a system like Ubuntu or, in my case, CentOS 5.5, right?

Does anyone know what the problem could be here, and how to fix it?

Thanks! :)

---

### Post by Allen.Lee@asu.edu on 2010-08-05
I got this working by editing my ~/.subversion/config and setting the password-stores variable, e.g.,
```

[auth]
password-stores = gnome-keyring

```

---

### Post by dirtreverse on 2011-03-14
Thanks Allen, that fixed it for me.

---

### Post by vw3366 on 2011-12-01
do you need to install the subversion-gnome?  I am running Ubuntu server 10  so I do not want to install the whole gnome package.

is it possible  to install subversion-gnome only?

sudo apt-get install subversion-gnome does not work for me.

Thanks

---

### Post by scotchie on 2012-05-31
I found there was an extra line near the bottom of *~/.subversion/config*, saying ```
password-stores =
``` In addition to setting "password-stores = gnome-keyring", I had to explicitly comment out the previous line. Nearly all lines are commented, obscuring the active settings. Try running ```
grep -v '^#' config
``` to see which lines are active.

On Ubuntu 11.10.

---

