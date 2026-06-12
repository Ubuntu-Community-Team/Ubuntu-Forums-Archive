---
title: "Boot Partiton"
date: 2009-11-25
forum: General Help
---

### Post by SebastienEndo on 2009-11-25
I have been following the steps from that page:
[https://help.ubuntu.com/community/Cr...onAfterInstall]("https://help.ubuntu.com/community/CreateBootPartitionAfterInstall")
truing to create a boot partition from which grub could run to boot either windows 7 or Ubuntu.

My problem is that I can't edit any of the files on my ubuntu partition because I can't get permission and I can't boot in either windows or ubuntu ...

gedit mnt/root/ect/fstab

won't work...

what should I do?

---

### Post by Gary Nored on 2009-11-25
You have to run gedit with correct privileges. 

Try this: 

  sudo gedit mnt/root/ect/fstab

Enter your password and you should be in.

---

### Post by SebastienEndo on 2009-11-25
thanks for the reply,
 I tried that, but I already have root privileges,

here is what I have:

root@ubuntu:#sudo gedit /mnt/root/ect/fstab

but a blank gedit comes up...

---

### Post by audiomick on 2009-11-25
I guess you have lost your root privileges, for whatever reason.

The first thing the author of the how to says to do in the terminal is 
```
sudo su
```
which gives you root privileges. Try dong that (again). It should persist until you shut the terminal window.

---

### Post by mechro on 2009-11-25
Is it as simple as ect should be etc?

---

### Post by audiomick on 2009-11-25
> **SebastienEndo said:**
> thanks for the reply,
 I tried that, but I already have root privileges,

here is what I have:

root@ubuntu:#sudo gedit /mnt/root/ect/fstab

but a blank gedit comes up...

that is what happens when the file isn't there that gedit is supposed to open.

The guide was written for 8.04. Maybe things have changed since then?

---

### Post by bodhi.zazen on 2009-11-25
> **SebastienEndo said:**
> thanks for the reply,
 I tried that, but I already have root privileges,

here is what I have:

root@ubuntu:#sudo gedit /mnt/root/ect/fstab

but a blank gedit comes up...

You should probably use gksu with graphical applications (rather then sudo).

---

### Post by mechro on 2009-11-25
@ SebastienEndo

Sorry to be a pain but can you just check you are typing **etc** and not **ect**.

---

### Post by audiomick on 2009-11-25
> **mechro said:**
> @ SebastienEndo

Sorry to be a pain but can you just check you are typing **etc** and not **ect**.

He isn't. Why didn't I notice that?

---

### Post by mechro on 2009-11-25
> **audiomick said:**
> He isn't. Why didn't I notice that?

... because I'm more anal than you?? ;):D

---

### Post by louieb on 2009-11-25
> **SebastienEndo said:**
> truing to create a boot partition from which grub could run to boot either windows 7 or Ubuntu.

You don't need to put /boot in its own partition for that. 
If your using Karmic and windows is not showing up in the grub menu try running
```
sudo grub-mkconfig
```

---

