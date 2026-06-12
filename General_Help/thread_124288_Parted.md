---
title: "Parted?"
date: 2006-02-01
forum: General Help
---

### Post by Elakt on 2006-02-01
it says it's installed on my ubuntu..and I can run it with sudo parted in console..but its only text stuff..is there any program with graphics? like Partition magic 8 for windows xp?

---

### Post by ps2gimp on 2006-02-01
Install GParted (Gnome) or QTParted (KDE), should be available in the "Add Applications" list.

---

### Post by xmastree on 2006-02-01
try **gparted**

---

### Post by Elakt on 2006-02-01
I am using it now..but its only pending my operations..not really doing them

---

### Post by cvcaelen on 2006-02-01
[QUOTE=Elakt]I am using it now..but its only pending my operations..not really doing them[/QUOTE]

there's an "apply" button

you did use it, didn't you?

---

### Post by munga_bill on 2006-02-01
Try GParted on its own live CD, that really works great and can do everything very easily.  You can download the .iso and burn it to a disk.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Elakt on 2006-02-01
[QUOTE=cvcaelen]there's an "apply" button

you did use it, didn't you?[/QUOTE]


yeah aply all operations..then it just starts to pending...does not a shit at all

---

### Post by Elakt on 2006-02-01
I downloaded this live cd iso...but must I burn it? I have no cd-r home..and hm is it possible to just run it in a console or something?

---

### Post by munga_bill on 2006-02-01
I downloaded this live cd iso...but must I burn it? I have no cd-r home..and hm is it possible to just run it in a console or something?> 
If you just right-click on the .iso file it should have an option something like 'burn to disk', I think that's all you have to do, but you'll need a CD of some kind. I don;t know of any ways to run an .iso file otherwise, but it might be possible.
Is there anywhere you can borrow a blank CD?

---

### Post by az on 2006-02-01
You cannot partition a disk that you are using.  That means a disk with anything mounted.  Even the live cd mounts your swap space.  


To partitition a disk, run the live cd and turn off your swap 

sudo swapoff -a

---

