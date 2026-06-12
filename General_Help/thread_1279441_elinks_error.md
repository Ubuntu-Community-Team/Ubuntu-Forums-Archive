---
title: "elinks error"
date: 2009-09-30
forum: General Help
---

### Post by prem1er on 2009-09-30
Just installed elinks with apt-get and I'm getting this error. Does anyone have a fix?

```
ERROR at /build/buildd/elinks-0.12~pre2.dfsg0/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
```

---

### Post by prem1er on 2009-10-01
bump

---

### Post by MillDaKill on 2009-11-05
I am getting the same error in ubuntu 9.10 64bit

```
~$ elinks 
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to connect() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
```

Elinks will eventually work after about 3-4 seconds of getting these error messages.  The really odd thing is that it works just fine for some of the accounts on my system, but others get these errors.

---

### Post by MillDaKill on 2009-11-05
> **MillDaKill said:**
> I am getting the same error in ubuntu 9.10 64bit

```
~$ elinks 
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to connect() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
ERROR at /build/buildd/elinks-0.12~pre5/src/main/interlink.c:329: The call to bind() failed: 13 (Permission denied)
```

Elinks will eventually work after about 3-4 seconds of getting these error messages.  The really odd thing is that it works just fine for some of the accounts on my system, but others get these errors.


Fixed the problem. I must have done a sudo elinks on my admin account and it messed up the permissions of the .elinks folder in my home dir.

to fix...  delete or chown the .elinks folder in your home space. 

Chown...
```

sudo chown -R user_name:user_name /home/user_name/.elinks

```

Delete...
```

sudo rm -rf /home/user_name/.elinks

```

---

### Post by MountainX on 2012-05-12
Thanks for the solution.

---

