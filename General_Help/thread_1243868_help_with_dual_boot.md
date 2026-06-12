---
title: "help with dual boot"
date: 2009-08-18
forum: General Help
---

### Post by rasengan127890 on 2009-08-18
Hello, I have just lost my ubuntu installation and i am purchasing a new hdd so i can have vista on 1 and ubuntu 9.04 on the other. i have been searching the internet on how to select which drive to boot from, but  cant seem to find how.Does anybody know how to dual boot ubuntu and vista from 2 drives without swaping? if so please tell me. it would be greatly appreciated :)

---

### Post by SoftwareExplorer on 2009-08-19
Usually, if you set up windows first, then ubuntu, Ubuntu will automatically set it up.

---

### Post by redhotfire on 2009-08-19
Install Windows first because windows will over write 
the boot sector, getting rid of the boot manager. 
By installing windows, then ubuntu, you can install LILO 
or Grub and it will see both operating systems.

---

### Post by SoftwareExplorer on 2009-08-19
> **redhotfire said:**
> Install Windows first because windows will over write 
the boot sector, getting rid of the boot manager. 
By installing windows, then ubuntu, you can install LILO 
or Grub and it will see both operating systems.
And so ubuntu can see windows and automatically make it a Grub entry. (Ubuntu uses grub by default)

---

### Post by nhanquy on 2009-08-19
> **rasengan127890 said:**
> Hello, I have just lost my ubuntu installation and i am purchasing a new hdd so i can have vista on 1 and ubuntu 9.04 on the other. i have been searching the internet on how to select which drive to boot from, but  cant seem to find how.Does anybody know how to dual boot ubuntu and vista from 2 drives without swaping? if so please tell me. it would be greatly appreciated :)

Boot the Ubuntu LiveCD

sign in as root.

Read: [http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

---

### Post by SoftwareExplorer on 2009-08-19
I should ask what you mean by 'lost' your ubuntu installation. It might be still there and just needs to be set up to boot, depending on what happened.

---

### Post by stinger30au on 2009-08-19
windows may have modiefed the boot up of the hdd

try using this

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

burn it to cd and boot off it

---

