---
title: "Installing openssh-server on Ubuntu from windows?"
date: 2010-05-24
forum: General Help
---

### Post by itxaka on 2010-05-24
Hello all!


I know I know, stupid thing but I am now really far away from my computer and would like to do some tasks on Linux.

Bad thing is..I reinstalled 10.04 a few days ago, and forgot to install openssh-server...duh!

So I am connected via terminal server with windows, but as soon as I reboot, Linux will boot and all access to it will be finished.

So is there any way to install an unattended openssh-server on the boot scripts without access to the computer and no way of writing the password?

I thought of mounting the partition with a Virtualbox linux machine , chroot into it and install it, but I don't think that will work, will it?

All kinds of crazy ideas are welcome :P

---

### Post by dino99 on 2010-05-24
*** All kinds of crazy ideas are welcome  ***

ok i give it a try : try meditation or eat some magic mushrooms  :mad:

---

### Post by itxaka on 2010-05-24
Nah, can't do meditation :P will think about the mushrooms thought

I actually manage to load up the partition on a virtualbox lucid machine but couldn't chroot onto it.
Seems that I forget that my ubuntu install is 64bit and my virtual machine is 32bit.

Still, I manage to edit crontab and add a root cron job to install openssh-server :D

Still have to try it. My terminal session got cut and it's not connecting now grrrrr

---

