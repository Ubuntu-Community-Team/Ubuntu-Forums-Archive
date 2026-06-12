---
title: "Suspending laptop from the command line as a normal user"
date: 2010-01-20
forum: General Help
---

### Post by geo909 on 2010-01-20
Hi all,

I would like to be able to suspend to disk or Ram from the command line. I can do it with the package 'hibernate' which works well, but it needs to be run as root:

```

jorge@flamingo:~$ hibernate-ram 
hibernate-ram: You need to run this script as root.
jorge@flamingo:~$ hibernate-disk
hibernate-disk: You need to run this script as root.

```

Do you know if there is any way that I can make this 
script run by normal users?

I am using a minimal version of 9.04 with openbox (crunchbang)

---

### Post by JohnFH on 2010-01-20
I have done something similar on my media PC.  I have automatic shutdown scripts which need to be run as root, so I edited the /etc/sudoers file to allow the shutdown command to be run as root, but without a password required.

Edit /etc/sudoers to add hibernate-run without requiring a password.

```

ALL  ALL = NOPASSWD: /usr/bin/hibernate-ram, /usr/bin/hibernate-disk

```

Note: ALWAYS use visudo to edit /etc/sudoers file.  visudo checks for gammatical errors before saving the changes.  A /etc/sudoers file with grammatical errors = a disaster!

---

### Post by geo909 on 2010-01-20
> **JohnFH said:**
> I have done something similar on my media PC.  I have automatic shutdown scripts which need to be run as root, so I edited the /etc/sudoers file to allow the shutdown command to be run as root, but without a password required.

Edit /etc/sudoers to add hibernate-run without requiring a password.

```

ALL  ALL = NOPASSWD: /usr/bin/hibernate-ram, /usr/bin/hibernate-disk

```

Note: ALWAYS use visudo to edit /etc/sudoers file.  visudo checks for gammatical errors before saving the changes.  A /etc/sudoers file with grammatical errors = a disaster!

Thanks a lot, that was very useful!!

---

### Post by geo909 on 2010-01-21
Oh well, I was mistaken: it didn't work..

Any ideas?

Thanks a lot..

---

### Post by geo909 on 2010-01-23
Bump?

I'm still required to give a password after doing that..
Any ideas?

Thanks..

---

### Post by rnerwein on 2010-01-23
hi
i guess your rule is overwritten !
try the following - it works for me
# sudo - exec a shell /bin/bash without a giving a password - edit
# /etc/sudoers and apend on the last line !!!! (after %admin ALL=(ALL): ALL
#              thats is why admin overlays rules before.

your_name ALL=NOPASSWD: /bin/bash

# and just as a hint -  use your login name for this option - don't allow this system wide

ciao

---

### Post by geo909 on 2010-01-23
> **rnerwein said:**
> hi
i guess your rule is overwritten !
try the following - it works for me
# sudo - exec a shell /bin/bash without a giving a password - edit
# /etc/sudoers and apend on the last line !!!! (after %admin ALL=(ALL): ALL
#              thats is why admin overlays rules before.

your_name ALL=NOPASSWD: /bin/bash

# and just as a hint -  use your login name for this option - don't allow this system wide

ciao

Hey, thanks a lot. But what that actually does is that it does not ask a password for *any* 'sudo' command, right?

---

### Post by freeball1 on 2010-01-23
Hi there
You might use ```
pmi action sleep
``` without sudo.

The Package is powermanagement-interface

---

### Post by geo909 on 2010-01-23
Hey, thanks a lot, that did the job! However it only suspends to ram. Can I use this to also suspend to disk? I couldn't find any man entry for this package..

---

### Post by freeball1 on 2010-01-25
Should also work with ```
pmi action hibernate
```
Not 100% sure though

---

