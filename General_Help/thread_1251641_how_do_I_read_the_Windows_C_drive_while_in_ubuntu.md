---
title: "how do I read the Windows C drive while in ubuntu?"
date: 2009-08-27
forum: General Help
---

### Post by Soujiro Seta on 2009-08-27
hello everyone. this question may sound pretty dumb, but well I need hep with it. thank you in advance. 

BTW I installed ubuntu with the new system. the one that lets you manage ubuntu with the installing and uninstalling programs tool of windows. if Im not wrong its called wubi or something like that.

---

### Post by abrari on 2009-08-27
WUBI?
the windows C drive is on /host folder.
try it.

---

### Post by sailthesea on 2009-08-27
Browse the disk and in your home directory you will find folder Host (CTRL H to see hidden folders/files)
This is the Windows partition this can be accessed from ubuntu Don't mess about in there though, your windows install supports the virtual disk that wubi uses Good way to find things out 
 And hello!

---

### Post by tgeer43 on 2009-08-27
I'm not familiar with the wubi installer but normally as long as your Windows drive/partition is mounted, you can access its files seamlessly.

Try: 'man mount' in a terminal for instructions on manually mounting a drive/partition or you can add an entry in your /etc/fstab file to have it automounted on startup.

There's lots of threads on here about mounting and fstab. Just do a little search and you'll have all the answers.

If you run into problems, post back here.

tgeer

---

### Post by Soujiro Seta on 2009-08-27
thanks! got it solved.

---

