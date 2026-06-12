---
title: "Error updating from 8.04 to 10.04 beta"
date: 2010-04-22
forum: General Help
---

### Post by megahost on 2010-04-22
When I tried to update my ubuntu, I received an error regarding the UUID not existing. When I updated, everything on the system was swell, but now I get the UUID does not exist. I reckon that ubuntu 10.04 does not need UUID. I can only run from the ubuntu shell with limited commands. I tried to edit the file /etc/default/Grub and it claimed to not exist. I have 2 separate versions of ubuntu on there, but hopefully it's using the grub installed from ubuntu 8.04. It says I'm using grub .97 beta. I am sure I have a brief idea of what to do. The problem is accessing the file necessary to do that. I will have to remove a line that says "LINUX_USE_UUID=true" or something like that. I don't know where that folder is. Apparently people say that its in /etc/default/grub. That doesn't exist for me. Please help Thanks MegaHost

---

### Post by chaosx9 on 2010-04-22
Well, i'm not really that good with it, but i'm thinking if there's a problem with the UUID, you should edit /etc/fstab and check the UUID of the mounting partition.

If you have a dualboot system set up, then i would use windows/mac to help out with it, like using a live cd to access the file for editing, while using gedit, and looking at the info of the partitions to check the UUIDs

You could also use SuperGrubDisk (helps me out a lot) see if that boots you into lucid, then update grub from there.

---

