---
title: "Add user with username as a number"
date: 2012-05-22
forum: General Help
---

### Post by thunderboltz on 2012-05-22
I am trying to create a user with the username as a number. Getting the following error:

```
abc@def:~$ sudo adduser --force-badname 377272
Allowing use of questionable username.
Adding user `377272' ...
Adding new group `377272' (1002) ...
Adding new user `377272' (1001) with group `377272' ...
useradd: group '377272' does not exist
adduser: `/usr/sbin/useradd -d /home/377272 -g 377272 -s /bin/bash -u 1001 377272' returned error code 6. Exiting.

```

How can I get it to accept the numbers only username? Also, why is Ubuntu preventing numbers only usernames by default? :confused:

---

### Post by dcstar on 2012-05-22
> **thunderboltz said:**
> I am trying to create a user with the username as a number. Getting the following error:

```
abc@def:~$ sudo adduser --force-badname 377272
Allowing use of questionable username.
Adding user `377272' ...
Adding new group `377272' (1002) ...
Adding new user `377272' (1001) with group `377272' ...
useradd: group '377272' does not exist
adduser: `/usr/sbin/useradd -d /home/377272 -g 377272 -s /bin/bash -u 1001 377272' returned error code 6. Exiting.

```

How can I get it to accept the numbers only username? Also, why is Ubuntu preventing numbers only usernames by default? :confused:

Linux usernames must **not** begin with numbers. Linux utilities like chown depend on a username starting with a letter to differentiate it from a UID.

```
man adduser.conf
```

---

### Post by Paqman on 2012-05-22
You could use a kind of reverse-1337 and call your user bllzlz.

---

