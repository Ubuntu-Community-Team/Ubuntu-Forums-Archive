---
title: "Partitioning question"
date: 2006-04-19
forum: General Help
---

### Post by Pete051 on 2006-04-19
When I set up my current system (Dapper) my brain was obviously taking a break because I created 4 primary partitions /boot /swap /home and /. The problem I have now is this, I'd like to try the new Gentoo distro but with 4 primary partitions I've nowhere to put it, I'm thinking of removing /home from fstab and creating an extended partition there for gentoo. Now if I do that will a new (empty) /home be created in / or an I looking at a new unstall?
Thanks
Pete :)

---

### Post by Prospero2006 on 2006-04-19
I don't know. That's an interesting question right there. 
I've always put my whole installation on a single partition, but I've 
heard creating a parition for /home is a good idea in case you need to reinstall the system.  

Here is my feeble logic:

      -I would suggest booting into dapper.
      -create a /home2 directory
      -cp -R /home /home2
      -umount /home
      -rm -R /home
      -mv /home2 /home
      -open up fstab
      -remove the entry for /home
      -Reboot
Wouldn't that free up the partition?

Pros

---

### Post by Pete051 on 2006-04-19
Hmm, when I try the umount /home command I get the device busy error :(

---

### Post by Prospero2006 on 2006-04-19
Boot your computer with a Knoppix CD. 
That will let you remove the home directory.

Pros

---

### Post by fdoving on 2006-04-19
[QUOTE=Prospero2006]I don't know. That's an interesting question right there. 
I've always put my whole installation on a single partition, but I've 
heard creating a parition for /home is a good idea in case you need to reinstall the system.  

Here is my feeble logic:

      -I would suggest booting into dapper.
      -create a /home2 directory
      -cp -R /home /home2
      -umount /home
      -rm -R /home
      -mv /home2 /home
      -open up fstab
      -remove the entry for /home
      -Reboot
Wouldn't that free up the partition?

Pros[/QUOTE]
Yes it would.

- Frode

---

### Post by Pete051 on 2006-04-21
Yeah the knoppix idea worked, I think in future I'll use LVM :) 
Thanks everybody

---

