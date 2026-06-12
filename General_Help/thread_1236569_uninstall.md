---
title: "uninstall"
date: 2009-08-10
forum: General Help
---

### Post by nevsky on 2009-08-10
I would like to uninstall Ubuntu using debain etch and get rid of the partition. If it is not possible to get rid of the partition I would still like to free the space. How would I go about doing this?

---

### Post by Andreas1 on 2009-08-10
i'm not sure what you mean by "using etch", is it installed on another partition? anyway, i would suggest using some live cd (not sure if debian can be used as one, ubuntu can) and formatting/removing the partition with gparted.

---

### Post by nevsky on 2009-08-10
Thanks for you help, Andreas1.
I originally had debian etch on my computer. It has too many issues that I am not able to deal with so I installed Ubuntu today. Accidentally I installed it in a separate partition with all but no space in it so I am not even able to update the os. So, I would like to remove debian and the partition or ubuntu and the partition or both while still retaining the data on my hard drive.

---

### Post by Andreas1 on 2009-08-10
so is your personal data on the same partition as one of your operating systems?

---

### Post by nevsky on 2009-08-10
unfortunately it is with debian etch in that partition, the ubuntu partition is too small to hold more than the OS. There is more on a separate partition but I believe that won't be affected.

---

### Post by Andreas1 on 2009-08-10
i would do the following:

boot from ubuntu cd: choose "start ubuntu without changing anything" or something like that rather than "install ubuntu"

copy all your personal data to that mentioned separate partition or some other place safe

start gparted (System > Administration > Partition Editor) and format or remove the partitions to your liking

---

