---
title: "Permissions of /var"
date: 2009-12-14
forum: General Help
---

### Post by TCSnyder on 2009-12-14
I did something dumb and now i cannot fix it.

i installed apache2 and it worked fine

but instead of changing permissions of /var/www i did it for /var/www/..

so now i have errors and stuff when i run sudo and gksu wont accept my password.

so i was wondering if someone could tell me what permissions are set on their /var.

this command should work and you can just post the output

```
ls -dRl
```

---

### Post by dcstar on 2009-12-14
> **TCSnyder said:**
> I did something dumb and now i cannot fix it.

i installed apache2 and it worked fine

but instead of changing permissions of /var/www i did it for /var/www/..

so now i have errors and stuff when i run sudo and gksu wont accept my password.

so i was wondering if someone could tell me what permissions are set on their /var.

this command should work and you can just post the output

```
ls -dRl
```

```
root@dc-master:/var# ls -dRl
drwxr-xr-x 14 root root 4096 2009-10-17 17:45 .
```

---

### Post by TCSnyder on 2009-12-14
dang, that wasnt it. i thought it would be this

ls -d (directories) -R (recursive) -l (long output)

can anyone tell me what i am doing wrong

---

### Post by TCSnyder on 2009-12-14
well everything seems to have been fixed with a restart,

---

