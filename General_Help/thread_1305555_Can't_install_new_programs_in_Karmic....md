---
title: "Can't install new programs in Karmic..."
date: 2009-10-30
forum: General Help
---

### Post by Kodiak Bear on 2009-10-30
Hello all. I recently installed 9.10 via the 'alternate installer' and it installed without a hitch.

Unfortunately, I can't get any programs via the software center. I can view various applications but there is no way to install them..

Any ideas on how to fix this?

---

### Post by dvlchd3 on 2009-10-30
Are you receiving any sort of error message when you try to install?

Can you install any packages via apt-get?  I.E.

```

sudo apt-get install package_name

```

---

### Post by Kodiak Bear on 2009-10-30
> **dvlchd3 said:**
> Are you receiving any sort of error message when you try to install?

Can you install any packages via apt-get?  I.E.

```

sudo apt-get install package_name

```

I don't know any of the package names..

I can't even begin to install any programs. There is no install button and it is 'greyed out' under file.

---

### Post by Crafty Kisses on 2009-10-30
Try running:
```
sudo apt-get install pidgin
```
I just want to see if you get any errors.

---

### Post by Kodiak Bear on 2009-10-30
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package pidgin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libpurple0 libpurple-bin
E: Package pidgin has no installation candidate

```

Eh...I didn't use the GUI installer and must of messed up something. I never had problems like these with Jaunty..

---

