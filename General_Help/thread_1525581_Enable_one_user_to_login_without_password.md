---
title: "Enable one user to login without password"
date: 2010-07-06
forum: General Help
---

### Post by okos on 2010-07-06
I am trying to enable my 6 year old to login without a password.
Currently, Kubuntu does not let me log him in without a password.
Your help would be much appreciated.
Thanks

---

### Post by Ozymandias_117 on 2010-07-06
There may be a better way... But you should be able to modify /etc/passwd you will have entries that look like:
```
user:x:1000:1000:user:/home/user:/bin/bash
```
find the one that has your child's login and remove the "x"
```
user::1000:1000:user:/home/user:/bin/bash
```

---

### Post by Firedrake445 on 2010-07-06
Could you use the guest account for him?

---

### Post by okos on 2010-07-06
> **Ozymandias_117 said:**
> There may be a better way... But you should be able to modify /etc/passwd you will have entries that look like:
```
user:x:1000:1000:user:/home/user:/bin/bash
```
find the one that has your child's login and remove the "x"
```
user::1000:1000:user:/home/user:/bin/bash
```

So I take it you do not have to edit /etc/pam.d/common-auth file to nollock?

See this link
[http://ubuntuforums.org/showthread.php?t=819198](http://ubuntuforums.org/showthread.php?t=819198)

---

### Post by okos on 2010-07-07
> **Firedrake445 said:**
> Could you use the guest account for him?

No, He wants his own account.
Thanks though

---

### Post by Ozymandias_117 on 2010-07-07
You shouldn't need to mess with anything else, but I'm not certain if it works in Ubuntu. The only time I've done that I was on a different distro.

---

### Post by cmcanulty on 2010-07-07
I found this
[http://www.jfriendly.net/other-interest/ubuntulinux/57-how-to-create-a-user-with-a-blank-password-in-ubuntu](http://www.jfriendly.net/other-interest/ubuntulinux/57-how-to-create-a-user-with-a-blank-password-in-ubuntu)
I need this for a library so I just put lots of restrictions and no password on library user account.

---

### Post by sisco311 on 2010-07-07
> **okos said:**
> I am trying to enable my 6 year old to login without a password.
Currently, Kubuntu does not let me log him in without a password.
Your help would be much appreciated.
Thanks

Edit the /etc/pam.d/kdm file to look like this:
```
#
# /etc/pam.d/kdm - specify the PAM behaviour of kdm
#
auth       required     pam_nologin.so
auth       required     pam_env.so readenv=1
auth       required     pam_env.so readenv=1 envfile=/etc/default/locale
**auth       sufficient   pam_succeed_if.so user ingroup nopasswdlogin**
@include common-auth
session    required     pam_limits.so
@include common-account
@include common-password
@include common-session

```

Then add the user to the **nopasswdlogin** group:
```
sudo gpasswd -a user nopasswdlogin
```

You may have to create the group first:
```
sudo addgroup nopasswdlogin
```

---

