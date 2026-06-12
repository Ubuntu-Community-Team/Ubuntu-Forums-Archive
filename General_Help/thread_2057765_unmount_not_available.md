---
title: "unmount not available"
date: 2012-09-14
forum: General Help
---

### Post by z5um on 2012-09-14
hi,


using lubuntu 12.04 and my problem is, i cannot use unmount because it's not there and i'm unable to install it.

I tried to install both of the following packages but both aren't there.

```
$unmount
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
```

```
$sudo apt-get install loop-aes-utils 
sudo: unable to resolve host august
Reading package lists... Done
Building dependency tree       
Reading state information... Done
loop-aes-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 167 not upgraded.

```

How do i unmount partitions?
Are there other commands? 
Is there another way to install unmount?

---

### Post by SlugSlug on 2012-09-14
umount not unmount ;)

---

### Post by ranger1021994 on 2012-09-14
> **z5um said:**
> hi,


using lubuntu 12.04 and my problem is, i cannot use unmount because it's not there and i'm unable to install it.

I tried to install both of the following packages but both aren't there.

```
$unmount
No command 'unmount' found, did you mean:
 Command 'umount' from package 'mount' (main)
 Command 'umount' from package 'loop-aes-utils' (universe)
unmount: command not found
```

```
$sudo apt-get install loop-aes-utils 
sudo: unable to resolve host august
Reading package lists... Done
Building dependency tree       
Reading state information... Done
loop-aes-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 167 not upgraded.

```

How do i unmount partitions?
Are there other commands? 
Is there another way to install unmount?


```
umount
```

Please mark it as SOLVED

---

