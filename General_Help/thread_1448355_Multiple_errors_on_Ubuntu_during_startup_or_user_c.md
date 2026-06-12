---
title: "Multiple errors on Ubuntu during startup or user creation"
date: 2010-04-06
forum: General Help
---

### Post by MachaHack on 2010-04-06
1. On login, I get an error: "Could not update .ICEAuthority" (not exact, can't copy/paste it. Is this in a log somewhere?). The permissions for my .ICEAuthority file are: 

```
-rwxr-xr-x  1 me me    91086 2010-04-06 18:58 .ICEauthority
```

and my home directory is: 

```
drwxr-xr-x 121 me  me  12288 2010-04-06 19:04 me
```

Two things that could cause this problem, according to google, yet they both look fine.

2. Immediately afterwards, I get the error: ```
gconf-sanity-check-2 exited with status 256
```.

I tried doing ```
chmod 755 /etc/gconf.xml.*
```, something google suggested would fix this. It didn't.

3. Trying to change a new user's password with passwd results in:

```
me@zero:/home$ sudo passwd macha
passwd: System error
passwd: password unchanged

```

And the following in /var/log/auth.log

EDIT:

Another possibly related error, is sometimes on opening it, Chrome prompts: Could not load user profile. (again, not exact wording)

```
Apr  6 19:06:40 zero passwd[30791]: pam_winbind(passwd:chauthtok): valid_user: wbcGetpwnam gave WBC_ERR_DOMAIN_NOT_FOUND
```

---

### Post by sisco311 on 2010-04-06
Change the permissions of the ~/.ICEauthority to 0600 or rename/remove the file.

Are you running Lucid? 

See this BUG: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/546874](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/546874)

---

### Post by MachaHack on 2010-04-06
> **sisco311 said:**
> Change the permissions of the ~/.ICEauthority to 0600 or rename/remove the file.

Are you running Lucid? 

See this BUG: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/546874](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/546874)

The comments for the bug fixed the issue with passwd. Renaming ~/.ICEauthority failed to solve the first two issues,

---

