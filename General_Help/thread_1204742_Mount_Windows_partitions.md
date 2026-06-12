---
title: "Mount Windows partitions?"
date: 2009-07-05
forum: General Help
---

### Post by gordon3913 on 2009-07-05
Using Ubuntu 9.04
I have just installed the latest updates and now I cannot view my Windows partitions. What is going on?
I was wanting to transfer some of my large files from Windows over to Ubuntu
but now I am stuck.

---

### Post by DeMus on 2009-07-05
> **gordon3913 said:**
> Using Ubuntu 9.04
I have just installed the latest updates and now I cannot view my Windows partitions. What is going on?
I was wanting to transfer some of my large files from Windows over to Ubuntu
but now I am stuck.

Try this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
```

sudo aptitude update
sudo aptitude install ntfs-config
```
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
They also appear when opening Nautilus.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" is checked and click OK.

---

### Post by gordon3913 on 2009-07-05
Thanks

---

### Post by DeMus on 2009-07-05
> **gordon3913 said:**
> Thanks

You're welcome.
I presume it works now.

---

