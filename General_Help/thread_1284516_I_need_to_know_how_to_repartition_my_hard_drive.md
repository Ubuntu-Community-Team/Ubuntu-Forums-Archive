---
title: "I need to know how to repartition my hard drive"
date: 2009-10-06
forum: General Help
---

### Post by grandpa2390 on 2009-10-06
I have Kubuntu installed but I there is a piece of software that I wish to use that will work on neither wine nor in VirtualBox. So I want to install Windows XP on a seperate partition that I can boot from. Problem is that I do not know how to create a new partition on my hard drive to install XP. the Microsoft install disc does not have a partition manager on it like Linux does.

---

### Post by Scunizi on 2009-10-06
You may have to do this from a live cd since the current file system can't be unmounted to resize while you use it.  So in a live cd go to the partition manager and carve out some space for XP.  Remember to google grub reinstall because after installing XP it will overwrite grub and you won't be able to get back to your ubuntu install.  Also, windows likes to be in a partition at the beginning of a drive.

---

### Post by grandpa2390 on 2009-10-06
Is there a way I can copy all of my kubuntu setting and just install windows then reinstall Kubuntu, and just restore everything. to a fresh install of Kubuntu?

---

### Post by Scunizi on 2009-10-06
You could use partimage or clonezilla .. clonezilla is the preferred.

---

