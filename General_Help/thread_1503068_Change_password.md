---
title: "Change password"
date: 2010-06-06
forum: General Help
---

### Post by za.zen on 2010-06-06
I'm trying to change my password, but the passwd command says my old password is too similar to the new one and won't let me.  

And that's true:  I'm reversing my current password so that it reads last to first rather than first to last.  Granted, that may not be safe, but I'm getting really annoyed that my system won't let me do it.  It's MY system after all, and MY responsibility if I use a weak password and get hacked.  

Is there any way to override this Microsoft-like behavior of the passwd command?  

Thanks.

---

### Post by viralmeme on 2010-06-06
> **za.zen said:**
> I'm trying to change my password, but the passwd command says my old password is too similar to the new one and won't let me
Try and disable PAM ..[ http://linux.die.net/man/8/pam_passwdqc]("http://linux.die.net/man/8/pam_passwdqc")

---

### Post by za.zen on 2010-06-06
> **ymitchell said:**
> Try and disable PAM ..[ http://linux.die.net/man/8/pam_passwdqc]("http://linux.die.net/man/8/pam_passwdqc")

PAM isn't running on my system.  At least, I can't see it if it is.

---

### Post by sisco311 on 2010-06-06
The easiest way is to change the password as root:
```
sudo passwd username
```

If you want to disable the extra checks for all users, then edit the /etc/pam.d/common-password file:
```

...
# here are the per-package modules (the "Primary" block)
password        [success=1 default=ignore]      pam_unix.so **obscure** sha512
...

```

and remove the obscure option. 

See:
```
man pam_unix | less +/obscure
```

---

### Post by aysiu on 2010-06-06
I think you can change it to a totally different password, and then change it to the one you want.

For example, if your old password is ```
Uyc@t>g$O@8k;#
``` then first change it to ```
X|)f''{Y()8("9
``` and then change it to ```
#;k8@O$g>t@cyU
```

---

### Post by za.zen on 2010-06-06
> **sisco311 said:**
> The easiest way is to change the password as root:
```
sudo passwd username
```

If you want to disable the extra checks for all users, then edit the /etc/pam.d/common-password file:
```

...
# here are the per-package modules (the "Primary" block)
password        [success=1 default=ignore]      pam_unix.so **obscure** sha512
...

```

and remove the obscure option. 

See:
```
man pam_unix | less +/obscure
```

> **aysiu said:**
> I think you can change it to a totally different password, and then change it to the one you want.

For example, if your old password is ```
Uyc@t>g$O@8k;#
``` then first change it to ```
X|)f''{Y()8("9
``` and then change it to ```
#;k8@O$g>t@cyU
```

Both excellent ideas.  It turns out a simple sudo in front of the passwd command will suffice, but changing the password to something totally different and then changing it back never even occurred to me.  It's actually quite clever.  

Thanks for the help, guys.  New password set and working.

---

### Post by mjones41 on 2010-11-01
But the real point is this is very Un Ubuntu like behavior.  It happened to me too, and it just makes the user angry.  OK by default you can warn the user their password is similar, but forcing them to pick another?

---

