---
title: "Sudo"
date: 2009-08-28
forum: General Help
---

### Post by cseguino on 2009-08-28
Hello,

I downloaded a VMWare image of Ubuntu 8.04 which has a user defined by user/user and no password for root.

When I try to execute 'sudo ls', I'm prompted for the password and then I select unter (empty string for the password). And then nothing happens. No error message because the password is incorrect and no list of files/directories.

When I try again but this time when prompted for the password, if I write anything I got invalid password message.

That's why I think the empty string is the good password, but the command is not executed.

Does anyone can help me please ?

Cheers,

Christophe Seguinot

---

### Post by aysiu on 2009-08-28
An empty string is **not** a good password.

You should reset your password to a proper one:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by aysiu on 2009-08-28
An empty string is **not** a good password.

You should reset your password to a proper one:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by blueridgedog on 2009-08-28
> **cseguino said:**
> 
That's why I think the empty string is the good password, but the command is not executed.

I can see that you mean "the correct password for this user on this virtual machine" rather than a desirable way to set passwords.

Can you change the password of the user account in question?

```
/usr/bin/passwd USER
```

Where USER is the default account?

---

