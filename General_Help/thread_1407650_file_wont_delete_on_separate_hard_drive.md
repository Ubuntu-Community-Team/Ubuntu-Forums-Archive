---
title: "file wont delete on separate hard drive"
date: 2010-02-15
forum: General Help
---

### Post by rastro123 on 2010-02-15
Hi I have a file on a separate hard drive and it wont allow me to delete it. Can anyone tell me how I navigate to it in the terminal so I can remove directory there? I plug my usb lead in and go /hoome/boo/Iomega_HDD (name of the hard drive) but I cant get there, it doesnt show up as a directory. Any help pls?

---

### Post by tom4everitt on 2010-02-15
External hard drives are usually mounted to /media or /mnt. Hence 

cd /media/

followed by

ls

would probably get you an idea of how to get there.

---

### Post by rastro123 on 2010-02-16
many thanks mate - worked a treat.

---

### Post by tom4everitt on 2010-02-17
Nice. Please choose thread solved from thread tools in the top of thread, its a good habit :)

---

