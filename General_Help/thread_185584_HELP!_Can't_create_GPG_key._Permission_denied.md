---
title: "HELP! Can't create GPG key. Permission denied"
date: 2006-05-31
forum: General Help
---

### Post by igor4u on 2006-05-31
```
igor@IgorSV:~$ gpg --gen-key
gpg (GnuPG) 1.4.2.2; Copyright (C) 2005 Free Software Foundation, Inc.
This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions. See the file COPYING for details.

gpg: failed to create temporary file `/home/igor/.gnupg/.#lk0x8124590.IgorSV.5842': Permission denied
gpg: block resource `/home/igor/.gnupg/secring.gpg': global error
gpg: failed to create temporary file `/home/igor/.gnupg/.#lk0x8126f08.IgorSV.5842': Permission denied
gpg: block resource `/home/igor/.gnupg/pubring.gpg': global error

```

Could you help me?

---

### Post by mlind on 2006-06-01
I couldn't reproduce this. Does gpg --list-keys output your keyring ok?

---

### Post by RAOF on 2006-06-01
Have you run "sudo gpg something" at any point?  It's possible that the permissions to ~/.gnupg are messed up.

What does ```
ls -lah ~/.gnupg
``` give?

---

### Post by igor4u on 2006-06-01
Here is output:
> 
igor@IgorSV:~$ gpg --list-keys
gpg: failed to create temporary file `/home/igor/.gnupg/.#lk0x8124590.IgorSV.8407': Permission denied
gpg: block recource `/home/igor/.gnupg/pubring.gpg': global error
gpg: no access to `/home/igor/.gnupg/trustdb.gpg': Permission denied
gpg: fatal: can't init trustdb: error in permission table
secmem usage: 0/0 bytes in 0/0 blocks of pool 0/32768
igor@IgorSV:~$ ls -lah ~/.gnupg
ls: /home/igor/.gnupg: Permission denied
igor@IgorSV:~$


---

### Post by mlind on 2006-06-01
RAOF is probably right, you've been running gpg using sudo or something.

does command
```

sudo chown -R igor4u.igor4u ~/.gnupg

```

fix the problem for you?
(replace 'igor4u' with your username)

---

### Post by igor4u on 2006-06-01
Thank you!
It works! )))

---

