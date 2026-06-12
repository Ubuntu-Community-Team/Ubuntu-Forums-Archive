---
title: "Expanding VirtualBox Disk (.vdi)"
date: 2010-02-22
forum: General Help
---

### Post by Muscovy on 2010-02-22
How can I expand a VirtualBox disk?

---

### Post by Baneblade on 2010-02-22
These should expand automatically for you when it begins to run out of room. Is this not happening, or are you anticipating a problem and checking in advance?

---

### Post by Joe Ker1086 on 2010-02-22
you set it up to expand or be fixed when you set up the initial virtual disk....not sure how to change that after-the-fact

---

### Post by Muscovy on 2010-02-22
I only gave it 5GB on creation. I think it's expandable, but I'm pretty sure that still means max of five.

---

### Post by przemoc on 2011-02-24
See [my answer]("http://bit.ly/f7sXTz") at SuperUser about expanding dynamic and fixed VDI files.

---

### Post by Habitual on 2011-02-24
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)

"The --resize option allows you to expand the capacity of an existing image; this increases the logical size of a virtual disk without affecting the physical size much.[33] This currently works only for the VDI and VHD formats, and only for the dynamically expanding variants. For example, if you originally created a 10G disk which is now full, you can use the --resize command to add more space to the virtual disk without having to create a new image and copy all data from within a virtual machine."

---

