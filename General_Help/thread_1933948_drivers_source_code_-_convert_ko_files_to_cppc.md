---
title: "drivers source code - convert ko files to cpp/c"
date: 2012-03-01
forum: General Help
---

### Post by athina on 2012-03-01
Hello,
I just shifted from opensuse to ubuntu. 
I was able to view and edit the drivers code. all driver files where inside /usr/src/linux/drivers/ and the files where cpp.
In ubuntu I bump into *.ko files and I don't know what to do or how to reverse them in c/cpp.
Is there any way to get a handle to c/ cpp code?
Thank you in advance,
Athina

---

### Post by TeoBigusGeekus on 2012-03-01
I don't think you can do this; ko files are _compiled_ kernel modules.

---

### Post by athina on 2012-03-01
> **TeoBigusGeekus said:**
> I don't think you can do this; ko files are _compiled_ kernel modules.

I thought so but I was hoping there was a reverse procedure..
So there is no way of getting access to drivers code? 
I want pci drivers to do specific stuff and I want to avoid writing a brand new pci express driver.. I was relying on modifying the existing driver that's why I need the cpp files..

---

### Post by TeoBigusGeekus on 2012-03-01
No easy answer on this, unless you can be more specific (and even then...)
What can I say; you could go through the kernel's source code :P

---

### Post by athina on 2012-05-18
Just for clarification, there is no way to convert *.ko files to source code.
A newbie question really.

---

