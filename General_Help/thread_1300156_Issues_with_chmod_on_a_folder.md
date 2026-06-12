---
title: "Issues with chmod on a folder"
date: 2009-10-24
forum: General Help
---

### Post by Horomancer on 2009-10-24
Hey there, I'm trying to set up a local samba network between my Ubuntu desktop and Vista laptop.
Samba works great, but when I try to access an external laptop that is connect to my desktop with my laptop I get a permission denied message.
ls -l spits this out

```
jackmo@jackmo-desktop:/media$ ls -l
total 36
lrwxrwxrwx  1 root       root           6 2009-10-08 05:58 cdrom -> cdrom0
drwxrwxrwx  2 4294967295 4294967295  2156 2008-02-17 19:04 cdrom0
drwx------ 22 jackmo     root       32768 1969-12-31 18:00 My Book

```

when i try to run
```

jackmo@jackmo-desktop:/media$ sudo chmod 777 "My Book"
```

I type in my password and it spits me back to a new command line, but the permissions stay the same. 

How do i get the My Book to be open to anyone on my network?

---

### Post by Horomancer on 2009-10-25
anyone?

---

### Post by orlox on 2009-10-25
> **Horomancer said:**
> anyone?

Probably no one answers because this is a hell of a strange problem...

Why do you have that folder under /media?? does it correspond to a removable device?

---

### Post by Vaphell on 2009-10-25
strange indeed, check if **chgrp jackmo "My Book"** changes anything

---

### Post by egalvan on 2009-10-25
> **orlox said:**
> Probably no one answers because this is a hell of a strange problem...

Why do you have that folder under /media?? does it correspond to a removable device?

Mounting under /media will result in auto-mounting, and an icon being placed on the desktop.
Some folks like this action.


Mounting under /mnt will result in no icon on the desktop.
This is my preference. 

Choice is good.

---

### Post by Horomancer on 2009-10-26
The folder is the external harddrive I have. I keep most of my media (music movies etc.) stored there. I would like to have access to it from any computer on my network, so I set up Samaba and changed it's file share properties to "guest". However it denies anyone without permission (everyone but my desktop it is directly connected to) to access the files though they are visible to everyone on the network.

Vaphell:
Tried what you reccommend and this is what I got

```
jackmo@jackmo-desktop:/media$ ls
cdrom  cdrom0  My Book
jackmo@jackmo-desktop:/media$ ls -l
total 36
lrwxrwxrwx  1 root       root           6 2009-10-08 05:58 cdrom -> cdrom0
drwxrwxrwx  2 4294967295 4294967295  2156 2008-02-17 19:04 cdrom0
drwx------ 22 jackmo     root       32768 1969-12-31 18:00 My Book
jackmo@jackmo-desktop:/media$ chgrp jackmo "My Book"
chgrp: changing group of `My Book': Operation not permitted
jackmo@jackmo-desktop:/media$ sudo chgrp jackmo "My Book"
[sudo] password for jackmo: 
chgrp: changing group of `My Book': Operation not permitted
jackmo@jackmo-desktop:/media$
```

I had this working all before I upgraded to 9.04 from 8.10
I remeber Samba was configured differently, so instead pf shared material just being available on the network, someone would have to login using a special login name and password I set that gave them the same rights and permissions as my user account. They could still only access material I told Samba to share, but those files only had to be 700 or similar for them to use, not 777 or what ever

---

