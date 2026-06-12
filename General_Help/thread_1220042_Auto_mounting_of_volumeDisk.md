---
title: "Auto mounting of volume/Disk"
date: 2009-07-22
forum: General Help
---

### Post by H.K.Murmu on 2009-07-22
Dear friend
How to  auto mount disk/ volume at the start up time

---

### Post by doas777 on 2009-07-22
> **H.K.Murmu said:**
> Dear friend
How to  auto mount disk/ volume at the start up time

well the traditional method is to add the device to the fstab file. the fstab contains information on what devices are expected and how to mount them.

the forum staff have put together a great tutorial:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by nnamdi on 2009-07-22
it is either u do it the traditional way by editing your fstab or go to your synaptics an install pysdm or open terminal 

```

sudo apt-get install pysdm

```

after which it has installed open terminal 
```

sudo pysdm

```

it runs the program but please be careful when doing these i advice you back your fstab first 
```

sudo cp /etc/fstab /etc/fstab.bak

```

---

