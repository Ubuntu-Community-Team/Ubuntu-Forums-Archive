---
title: "have a bash at mount drive"
date: 2010-05-14
forum: General Help
---

### Post by sevenearths on 2010-05-14
I have a bash script that mounts a drive before running a virtualbox instance of win xp on that drive. It looks like this:

```
#! /bin/sh
sudo mount /dev/sda5 /media/Extra
virtualbox -startvm WindowsXP
```

Can I mount the drive without sudo and so that I can unmount it from nautilus, and have error checking to make sure the drive hasn't been mounted before the script is run?

!!! ADDITION ADDITION ADDITION !!!

I had to run:

```
sudo mkdir /media/Extra
```

just so the mount command would work. Surely thats not the best way to be doing things?

---

### Post by sevenearths on 2010-05-16
anybody?

---

### Post by sevenearths on 2010-05-20
hummmmmmmm!

---

