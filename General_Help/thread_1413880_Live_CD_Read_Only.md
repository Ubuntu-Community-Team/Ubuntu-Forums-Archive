---
title: "Live CD Read Only"
date: 2010-02-23
forum: General Help
---

### Post by lemurid on 2010-02-23
I'm trying to use a Ubuntu 9.10 Live CD to fix the installation. But somehow i just can't mount my Hard Drive in rw. 

sudo mkdir /media/HHDZ
sudo mount /dev/sdc1 /media/HHDZ

(no errors till here)

sudo gedit /media/HHDZ/boot/grub/grub.cfg

Clicking on save results in the following error

Couldn't save. You are trying to save to a read only filesystem

---

### Post by gmargo on 2010-02-23
That is quite irritating.  The problem is due to the permissions on the **grub.cfg** file.  **gedit** gives a misleading error message and offers no option to write to the file anyway (like **vim**'s ":w!" command.)

If you make the file writeable (**chmod 644 grub.cfg**) then **gedit** will work.  Make a backup copy first.

---

### Post by lemurid on 2010-02-23
> **gmargo said:**
> 
If you make the file writeable (**chmod 644 grub.cfg**) then **gedit** will work.  Make a backup copy first.

Thank you. Worked like a charm

---

