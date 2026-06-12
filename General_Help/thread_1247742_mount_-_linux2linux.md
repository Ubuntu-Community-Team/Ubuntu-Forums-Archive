---
title: "mount - linux2linux"
date: 2009-08-23
forum: General Help
---

### Post by cbear on 2009-08-23
I have just built a new linux machine, so now I have two.  I have done lots of mounting in the past from linux to windows but have never tried to mount another linux machine (non samba).  How to I mount between the two machines ?

I tried

I created a mount point on old.machine  

mkdir /media/mount2

I ran:

mount <ipaddress_newmachine> /home/tom/

Doesn't seem to work.  Do I have to specify the type of file system (e.g. cifs) ?  Not sure what to do and 99% of the docs out there talk about mounting windows partitions.

---

### Post by spiderbatdad on 2009-08-23
the machine you want to access should be running a file server or set up openssh. You can then mount the entire filesystem via sftp. Use the connect to server option under the places menu. You choose ssh for server type then you really only need the ip of the machine and username. See the openssh documentation. It is easy to set up once you get started.

---

