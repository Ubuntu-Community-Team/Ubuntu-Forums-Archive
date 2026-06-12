---
title: "upgrade error"
date: 2010-09-18
forum: General Help
---

### Post by bilgee0629 on 2010-09-18
When I tried to upgrade my xubuntu 10.04 , I got this error

dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'x11proto-core-dev':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)

What should i do???):P

---

### Post by Rubi1200 on 2010-09-18
If you run ```
sudo dpkg --configure -a
``` do you still get errors?

---

### Post by bilgee0629 on 2010-09-18
> **Rubi1200 said:**
> If you run ```
sudo dpkg --configure -a
``` do you still get errors?

still getting same error

---

### Post by Rubi1200 on 2010-09-18
Have you tried reinstalling the package (x11proto-core-dev)?

I would look in the package manager first and see if it is there and then maybe try reinstalling.

---

### Post by bilgee0629 on 2010-09-18
I renamed available to another name, then created a file which named available, so it worked well :p

---

### Post by Rubi1200 on 2010-09-18
Ok, if it worked it worked :)

---

