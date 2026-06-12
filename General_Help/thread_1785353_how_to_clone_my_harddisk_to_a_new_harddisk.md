---
title: "how to clone my harddisk to a new harddisk"
date: 2011-06-18
forum: General Help
---

### Post by j.jansen on 2011-06-18
how can I clone my installed ubuntu to a new harddisk?
with 32bit ubuntu I have used:tar cvpzf -> create a tar file on my external nas system.
after that I have done a restore   tar xvpfz  - worked with 32 bit.
Alternative I have mounted both disks and via another linux partition I have used:
cp -rvbdR /source/* /target

both methodes worked with ubuntu 32 bit.
With 64 bit ubuntu I can NOT get it to work.
error message after booting the clone: /var/lib/gdm/.ICEauthoriy ..

I can see that /source/var/lib/gdm has different rights as /target - will be part of the problem.
This did not happen with the 32 bit ubuntu - but why ?:(

Who has ideas?
I assume the tar and cp run into the same problem, what is different by 64 bit ubuntu?

---

### Post by Dngrsone on 2011-06-18
I use a program called HDClone to clone a disk, bit-for-bit, to another drive.

Comes in handy when upgrading my laptop to a larger drive and I want to keep a working Windows partition.

---

### Post by Rubi1200 on 2011-06-18
Take a look at Clonezilla as another possible tool for the job:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by oldfred on 2011-06-18
You can try resetting, but some find even that does not work.

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 600 $HOME/.ICEauthority

Natty .ICE issues work around
[http://ubuntuforums.org/showthread.php?t=1738580](http://ubuntuforums.org/showthread.php?t=1738580)
[http://ubuntuforums.org/showthread.php?t=1746144](http://ubuntuforums.org/showthread.php?t=1746144)

one user had this work:

sudo apt-get install gnome-session

---

