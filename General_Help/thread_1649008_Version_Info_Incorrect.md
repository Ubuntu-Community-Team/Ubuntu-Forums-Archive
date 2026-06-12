---
title: "Version Info Incorrect"
date: 2010-12-19
forum: General Help
---

### Post by spessog on 2010-12-19
Hello,

I am using ubuntu Version 10.10.  I always apply all important security updates and recommended updates.  When I checked the version of my software using the system->"About ubuntu" drop down, it tells me that I am using version 11.04 which "was" released on April 2011.  Is this a known issue?  Thanks, Scott.

---

### Post by karthick87 on 2010-12-19
What is the output of,

```
lsb_release -a
```

---

### Post by howefield on 2010-12-19
It's a known bug.

The link to which is posted elsewhere on these forums.

Here it is
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)

---

### Post by spessog on 2010-12-19
scott@mookie:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

---

### Post by spessog on 2010-12-19
> **howefield said:**
> It's a known bug.

The link to which is posted elsewhere on these forums.

Here it is
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/690248)



Thanks for the info!  I figured that it was a bug.

---

