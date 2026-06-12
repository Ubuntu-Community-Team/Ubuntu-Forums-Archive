---
title: "HIDE spamd as login account"
date: 2012-07-03
forum: General Help
---

### Post by frogotronic on 2012-07-03
from lightdm?

anyone?

---

### Post by matt_symes on 2012-07-03
Hi

> **cement_head said:**
> from lightdm?

anyone?

You cannot use the users.conf file in lightdm to hide individual users.It's hide all of the or none of them (if using the lightdm configuration files). I came accross this a little while ago explaining why. 

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/857651](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/857651)

The only way i know to hide a user is to ensure the UID of the user you want to hide is less than 500. It will then be seen as a system user and be hidden from the greeter.

Kind regards

---

### Post by frogotronic on 2012-07-05
> **matt_symes said:**
> Hi



You cannot use the users.conf file in lightdm to hide individual users.It's hide all of the or none of them (if using the lightdm configuration files). I came accross this a little while ago explaining why. 

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/857651](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/857651)

The only way i know to hide a user is to ensure the UID of the user you want to hide is less than 500. It will then be seen as a system user and be hidden from the greeter.

Kind regards

Can't seem to figure out how to log spamd out before changing the UID.

- CH

---

### Post by matt_symes on 2012-07-05
Hi

Boot into the recovery console from the GRUB menu and do it from there.

Kind regards

---

### Post by frogotronic on 2012-07-06
> **matt_symes said:**
> Hi

Boot into the recovery console from the GRUB menu and do it from there.

Kind regards

Nope - I get an error "cannot establish passwd lock"

- CH

---

### Post by matt_symes on 2012-07-06
Hi

Did you remount the drive read/write in recovery mode ? That may be the problem.

```
mount -o remount,rw /
```

Then try to change the UID.

Kind regards

---

### Post by frogotronic on 2012-07-07
Thanks, that did it!

- CH

---

### Post by frogotronic on 2012-07-11
Hello,

  For those of you experiencing the same problem, here's the complete solution.

1) Boot your machine (hard boot) and hold down the left SHIFT key.
2) Choose "Boot into Recovery Mode"
3) Choose "Drop into a Root Shell"
4) Enter your passwd
5) Enter the following code:
[INDENT]```
mount -o remount,rw /
usermod -u 499 spamd
```[/INDENT]
6) type "exit"
7) Choose "resume nomral boot sequence"

- CH

---

