---
title: "Wubi install on vista data partition - cannot see data"
date: 2010-06-08
forum: General Help
---

### Post by clhb on 2010-06-08
Hi,

I've installed wubi on my D: partition of a vista os.  Vista is installed on the C:

I can see the vista partition if i mount it but can only see the wubi 10.04 system files on the data partition (D: ).  No option to mount it either.

Also curious to know if its possible to automatically mount the c: on startup.

Bit of a noob so go easy on me!

---

### Post by unmole on 2010-06-08
Open any nautilus window and hit Ctrl+L. Now thype in /
You will see a folder named host. This is your D: You might want to drag it to the sidebar and make a shortcut under places. Take a look at [this]("http://ubuntuforums.org/showthread.php?t=785263") for your second question.

---

### Post by philinux on 2010-06-08
From here.
[http://wubi-installer.org/faq.php#use](http://wubi-installer.org/faq.php#use)

> Can I access my Windows files from a Wubi installation?

Yes, the Windows partitions will be available within the directories /host and /media.


---

### Post by clhb on 2010-06-08
Thanks!  All in order now (pending reboot)

---

