---
title: "gParted+Ubuntu: Extra swap, unsure if I can delete partition..."
date: 2011-10-12
forum: General Help
---

### Post by brightJoker on 2011-10-12
Hey all,
I have an extra swap partition from a previous install, listed at /sda5, in /fstab, it says my swap being used is on /sda7.  When I boot in gParted live, I go to delete the extra swap at /sda5, but then it renames all my sdas (/sda5 becomes /sda4, etc.)  I know many config files point to "/sdaX," so my question is, if I delete the extra swap and it relabels my partitions, will this break my OS' or need any repairing/editing after?

---

### Post by TeoBigusGeekus on 2011-10-12
> **brightJoker said:**
> Hey all,
I have an extra swap partition from a previous install, listed at /sda5, in /fstab, it says my swap being used is on /sda7.  When I boot in gParted live, I go to delete the extra swap at /sda5, but then it renames all my sdas (/sda5 becomes /sda4, etc.)  I know many config files point to "/sdaX," so my question is, if I delete the extra swap and it relabels my partitions, will this break my OS' or need any repairing/editing after?

You could use uuid's for your fstab file.
What other config files do you mean?

---

### Post by ajgreeny on 2011-10-12
> **TeoBigusGeekus said:**
> You could use uuid's for your fstab file.
What other config files do you mean?
Unless the OP has made manual changes to the /etc/fstab file it will already use UUIDs, unless I am mistaken.  There are comments such as 
```
# / was on /dev/sda1 during installation
# /home was on /dev/sda2 during installation
# swap was on /dev/sda5 during installation
``` but I don't think fstab has actually used /dev/sdx# naming for several years., and like you, I can not think of any other config files that still use them.

---

### Post by brightJoker on 2011-10-12
Ok cool, I really only knew of /fstab and it does use the UUID's, just wanted to double check before I just went and reformatted.  Thanks for the input!

---

