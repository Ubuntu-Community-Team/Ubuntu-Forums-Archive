---
title: "mount.cifs, kerberos and sudo"
date: 2010-11-16
forum: General Help
---

### Post by Causer1984 on 2010-11-16
Hello,

mount.cifs used to be able to work with kerberos tickets so long as I changed the binary to suid root. I understand why this may have fallen out of favour but since Meerkat, I am unable to get mount.cifs to mount using kerberos and sudo.

# Non sudo mount.cifs with/without suid root
```
$ mount.cifs //server/share/directory ~/central -o sec=krb5
mount.cifs: permission denied: no match for /home/CauserC/central found in /etc/fstab
```

# Sudo mount.cifs with/without suid root
```
$ sudo mount.cifs  //server/share/directory ~/central -o sec=krb5
mount error(126): Required key not available
```

I do definitely have a kerberos ticket, and both klist and "sudo klist" show it to me.

Now, it does work if I do a "sudo kinit $USERNAME." Then a sudo mount.cifs mounts the share no problem. This is obviously less than ideal because it involves typing in a password again, and subsequent non sudo klists result in:

```
$ klist
klist: Credentials cache permissions incorrect while setting cache flags (ticket cache FILE:/tmp/krb5cc_10009_8ZePnt)
```

I'm tempted to file this as a bug report but wanted to check in here first to make sure that I'm not doing anything stupid. As I say, I never tried this in Lucid as suid root worked fine.

Any help appreciated

Chris

---

