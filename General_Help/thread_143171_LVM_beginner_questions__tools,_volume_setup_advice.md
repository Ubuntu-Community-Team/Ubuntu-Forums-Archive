---
title: "LVM beginner questions:  tools, volume setup advice"
date: 2006-03-11
forum: General Help
---

### Post by IDigOnSwine on 2006-03-11
Hi everyone,

I'm new to both Ubuntu and LVM, and I have a couple of questions on my setup and working with LVM.

I'm on a system completely devoted to Ubuntu, and I just did a "erase and install using lvm" during installation.  I selected the defaults, and created a boot partition, and then an LVM partition for the remainder of the drive (300G).  In order to get started quickly, I just went with the defaults (2 G swap, the rest for root ext3).  Now I'm thinking that I should separate out the root volume into root, /home, maybe a /var and /usr.  I plan on using this system for some file sharing (files of a few megs each), and some web app development (so DB, app server, etc. to be installed).  So:

1)  Are there any GUI tools available for managing LVM logical volumes?

2)  I noticed in these forums that a lot of people suggest just leaving the entire drive as one big root partition.  Should I not bother splitting this root logical volume up?

3)  Will I be able to split the root volume up while running off of my normal setup, or will I need to boot from a LiveCD?

Thanks for the help.  FWIW, I'm really impressed with Ubuntu thus far.

---

### Post by steevc on 2006-03-17
I've just been through a similar process on my new 250GB drive. This was my first Breezy install and I had hoped that the LVM part would allow sub-dividing the partition. I like to have /home and /data partitions so that I can preserve those should I do another install. I went for LVM this time as previously I ran into space problems with my / partition and I hope it will allow me to cope with future changes in requirements.

I think I've read that there is a lack of LVM GUI tools, but a few hints on the command line may be enough to sort us out.

---

### Post by ameerirshad on 2006-03-17
I have twe hard drives and on both I have LVM running, however I can't seem to gain access to one or the other from the systems. I have tried to mount the harddrives, also I have tried to use disks-admin, this however claims that my /dev/hdb6 has no filesystem, this is however the lvm filesystem. How can I get the disks-admin or my ubuntu-system to recognize this /dev/hdb6 as lvm?

---

