---
title: "Partition Viewer?"
date: 2009-10-12
forum: General Help
---

### Post by kabanta on 2009-10-12
is there a simple, graphical viewer that will show the existing partitions (*and their sizes in mb/gb*) on my machine?

note: i am looking for an alternative to gparted/qparted (that is, something other than partition *editors*)

if there is no gui-based alternative, what is the simplest way to list the partitions *and their sizes in mb/gb* from the command line?

thanks.

---

### Post by fluffman86 on 2009-10-12
You want gparted.  It will let you view everything without making changes.

---

### Post by kabanta on 2009-10-12
> **fluffman86 said:**
> You want gparted.  It will let you view everything without making changes.

i know what gparted will do. i am asking about ALTERNATIVES.

---

### Post by fluffman86 on 2009-10-12
sudo parted -l

edit: that's a lower case L

---

### Post by kabanta on 2009-10-12
> **fluffman86 said:**
> sudo parted -l

edit: that's a lower case L

brilliant! thanks.

---

