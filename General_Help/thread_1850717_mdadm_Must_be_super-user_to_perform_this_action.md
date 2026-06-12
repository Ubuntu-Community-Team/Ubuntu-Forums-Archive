---
title: "mdadm: Must be super-user to perform this action"
date: 2011-09-27
forum: General Help
---

### Post by josiahrulez on 2011-09-27
Ok, well im attempting to create a mdadm Raid0 Array, with 3x1.5tb HDDs, this is the command im using


*mdadm --create /dev/sdb1 /dev/sdc1 /dev/sdd1 --level=raid0*

but it comes up with an error (i think it wants admin rights?)

*mdadm: Must be super-user to perform this action*

what can i do to give it admin rights?

also this is the first time I've played around with linux so any help is appreciated.

---

### Post by lisati on 2011-09-27
The usual way to temporarily elevate your user's admin rights in Ubuntu is with the "sudo" command, e.g.
```
sudo mdadm --create /dev/sdb1 /dev/sdc1 /dev/sdd1 --level=raid0
```

---

### Post by josiahrulez on 2011-09-27
> **lisati said:**
> The usual way to temporarily elevate your user's admin rights in Ubuntu is with the "sudo" command, e.g.
```
sudo mdadm --create /dev/sdb1 /dev/sdc1 /dev/sdd1 --level=raid0
```

Thanks for that, i always used sudo for the "sudo apt-get" but never knew it was for admin tasks in command line.

also, my mdadm command doesn't work. so if you could help with that also.

*sudo mdadm --create /dev/sdb1 /dev/sdc1 /dev/sdd1 --level=raid0*

error message
*mdadm: device /dev/sdb1 exists but is not an md array.*

---

### Post by Azdour on 2011-09-27
Hi,

There is an old thread here but I think the mdadm command has not changed much:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

After the --create it's expecting the raid array name, e.g. /dev/md0. The list of hdd's you want to use normally appears at the end of the mdadm command.

---

