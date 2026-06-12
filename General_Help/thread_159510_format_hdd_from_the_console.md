---
title: "format hdd from the console"
date: 2006-04-13
forum: General Help
---

### Post by leftyman on 2006-04-13
Hello


The application from the administration menu is refusing format a NTFS partition into ext3 (I have saved all my data! 8-) . It gives me the warning that I will loose all my data, I click on continue and it just exits.


Is it possible to format /dev/sda1 in ext3 format from the console?

thanks

---

### Post by dcstar on 2006-04-13
[QUOTE=leftyman]Hello


The application from the administration menu is refusing format a NTFS partition into ext3 (I have saved all my data! 8-) . It gives me the warning that I will loose all my data, I click on continue and it just exits.


Is it possible to format /dev/sda1 in ext3 format from the console?

thanks[/QUOTE]
Was the partition unmounted?

---

### Post by leftyman on 2006-04-13
Hi

the format button is greyed until you unmout it, so it was unmounted

thanks

---

### Post by dcstar on 2006-04-13
[QUOTE=leftyman]Hi

the format button is greyed until you unmout it, so it was unmounted

thanks[/QUOTE]
parted is a command line tool that may do what you want, but it looks a little complicated.

---

### Post by pitkali on 2006-04-13
[QUOTE=leftyman]Is it possible to format /dev/sda1 in ext3 format from the console?[/QUOTE]
Naturally. It would be something like:
> sudo mkfs.ext3 /dev/sda1
It would be a good idea to change also the partition type indicated in partition table to Linux. You may want to use cfdisk for that - quite userfriendly text application.

Regards,

---

