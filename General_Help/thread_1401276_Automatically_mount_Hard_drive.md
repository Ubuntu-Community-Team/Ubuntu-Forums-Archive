---
title: "Automatically mount Hard drive?"
date: 2010-02-07
forum: General Help
---

### Post by louscookies on 2010-02-07
Does anyone know (if possible) how I might be able to make one of my hard drives automatically mount on Start-up? I don't mind having to mount it every time but it does get slightly annoying especially when everytime I have to enter the admin password.

Any ideas?

---

### Post by cjhabs on 2010-02-07
Check out the man page for fstab - that'll do the trick.

---

### Post by louscookies on 2010-02-07
I would, if I knew what that was. Sorry can I get an explanation please? :)

---

### Post by cjhabs on 2010-02-07
from a terminal type:
man fstab
This gives an explanation of the /etc/fstab control file that controls mounting disks at boot time.

---

### Post by louscookies on 2010-02-07
Okay I read it, I still don't know what to do though.

---

### Post by n0dix on 2010-02-07
There are many threads about this in the forum. Please, look first.

---

### Post by louscookies on 2010-02-07
I have done. Not alot of instructions are clear for someone as new to the Terminal as I am and I don't want to edit the fstab file when I have no idea how. Hmmm.

---

### Post by ankspo71 on 2010-02-07
Hi,
You can install a package called pysdm (Storage Device Manager). You can find it in Ubuntu Software Center and in Synaptic Package Manager.

Once you get it installed, go to System > Administration > Storage Device Manager and open it.  After identifying the drive partition you want to mount automatically, there are only 2 options that you need to set.  see the image below.
hope this helps.

---

### Post by ankspo71 on 2010-02-07
I forgot the image :p

---

### Post by louscookies on 2010-02-07
Thank you you've been a great help :D !

---

