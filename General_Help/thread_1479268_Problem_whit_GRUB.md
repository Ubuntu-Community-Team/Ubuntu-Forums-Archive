---
title: "Problem whit GRUB"
date: 2010-05-10
forum: General Help
---

### Post by TripBR on 2010-05-10
Hello guyz!

I have two hard disks, Ubuntu 10.04 was installed on SDB (second disk), than I formatted SDA and tryed to reinstall grub, but when the computer boot there is just the comand line from GRUB. Than I need to manually type the codes:

```
root (hd1,1)
configfile /boot/grub/grub.cfg
```

How can I fix this?

Tanks!

---

### Post by deanhopkins on 2010-05-10
If you can currently get into your system, enter the following commands into a terminal:

```
sudo grub
```

You will be presented with a ">" .. this is normal.

```
root (hd1,1)
```

```
setup (hd0)
```

This will install grub to your Master Boot Record. If you do not want to install to the MBR, you can change setup to (hd1,1) point the BIOS to boot from there


If you cant boot into your system, run the previous commands as normal in a live CD environment.

EDIT: For future reference, if you are not sure where your grub config file is (where grub is installed), you can find it by typing:

```
find /boot/grub/stage1
```

in the grub command line - this will return a value such as (hdx,#)

---

### Post by TripBR on 2010-05-10
Tanks for the Tip, but this is for Grub 1.5. I'm using Grub 2 that comes whit Lucid.

---

### Post by oldfred on 2010-05-10
If in BIOS or key at startup change to boot sdb. If grub is in sdb it will boot.

---

### Post by AdotB on 2010-05-10
I don't know if this will help, but have you looked at grub-install?

---

