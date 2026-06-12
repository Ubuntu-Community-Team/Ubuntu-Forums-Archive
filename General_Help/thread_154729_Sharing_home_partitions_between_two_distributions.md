---
title: "Sharing /home partitions between two distributions"
date: 2006-04-03
forum: General Help
---

### Post by tgoose on 2006-04-03
Now I've got both Ubuntu and Fedora Core on the same machine (I figured when one was a bit iffy (and for Ubuntu on my hardware, that's got to be wireless WEP & printing!) the other one could work), and I'm wondering firstly if it's possible to change the setup of Fedora Core so that instead of mounting the partition I originally intended on my external drive as /home, it could use the internal partition that already has data & files on, and secondly if there are any issues with this (e.g. differing builds of programs conflicting settings). 

Thank you :)

edit: after a bit more looking it seems that, in general it is OK to share the /home partition. So what I'm really looking for is a way to do this now, having not actually done it on the install (my external /home has nothing on I want to keep, so I don't need to copy anything across)

---

### Post by CloudBuilder on 2006-04-03
You can afterwards always make new entries in the FSTAB and link them to maps.
However I think HOME is not the right map.

I have 3 boxes running, so I reservedone of the partitions and made in all distro's a map called MyDocs and . I made submaps with the name of the distro. Then I put all kind off files in them that I would need in case of trouble. If one distro fades away, I can repair it with the things I have in that map from the other distro.

I also have a map in (ubuntu)mnt called suse, this map is coupled to the Suse distro. And in Suse-mnt a map called Ubuntu, so I can alway access a distro from another distro. Tha's verry nice If you need X setup files or the settings from fstab etc.

CloudBuilder

---

