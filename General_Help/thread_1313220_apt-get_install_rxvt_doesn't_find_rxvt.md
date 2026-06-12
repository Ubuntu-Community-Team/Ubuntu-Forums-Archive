---
title: "apt-get install rxvt doesn't find rxvt"
date: 2009-11-03
forum: General Help
---

### Post by BigFlatBrook on 2009-11-03
One on system, 

   sudo apt-get install rxvt

works as expected.  But on a different (newly created) system,

   sudo apt-get install rxvt

is unable to find the rxvt package.  The message is

sudo apt-get install rxvt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package rxvt

Maybe if I changed the package server??  How would I do that?

Thanks

---

### Post by liquidbee on 2009-11-03
```
cat /etc/sources.list

```

Reply with the output.

---

### Post by sisco311 on 2009-11-03
rxvt is in the universe repo, you have to enable the repo first:
```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install rxvt
```

---

### Post by BigFlatBrook on 2009-11-03
First, I did

sudo software-properties-gtk -e universe

and got back a warning.

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

But then "sudo apt-get update" worked anyway.

After which "sudo apt-get install rxvt" worked.

I will post my sources.list if that still helps, but otherwise, I think I'm good now.

Thanks.

---

