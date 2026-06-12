---
title: "ld.so preload error on ubuntu 10.04"
date: 2010-08-07
forum: General Help
---

### Post by ambush276 on 2010-08-07
basically i have the pam face authentication thing installed.

i have ubuntu 10.04 installed with the gdm 2.28 package (not the full desktop just the sudo apt-get install gdm)

i have LVM encryption with the password prompt before bootup.. after i type that usually i get this error

```


[LIST=1]
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[*]ERROR: ld.so: object  '/usr/lib/libv41/v411compat.so' from /etc/ld.so.preload cannot be  preloaded: ignored.
[/LIST]
          
```it happens about 6 times then boots up... and the face authentication does not work....

i had a VM machine running without LVM encryption and i set it up the same way and i had no errors???

what is wrong?

Thanks!

---

### Post by ambush276 on 2010-08-07
ok i got the error to stop.. but the module will not work when i startup..

basically i click on my name.. and it flashes to the password screen and says face authentication failed????

what is goin on?

---

