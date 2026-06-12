---
title: "Creating ghost image?"
date: 2010-05-22
forum: General Help
---

### Post by m00nshine on 2010-05-22
Hello,
 
I have Win 7 and ubuntu 9.10 dual booted on a 80gb hardrive. There is also a 200 gb hd in my system but I have not formatted it yet. When I use ghost32 to create an image it warns me to run fsck on the Linux installation because it was not unmounted properly or something along those lines. If I force the image creation then write it to the 80gb HD grub will begin to load as usual but then the sytem will reboot continuously. Do I have to boot from the installation cd, run terminal, and issue a fsck command? Please help, rebuilding my system gets old!

---

### Post by Skorzen on 2010-05-22
Did you tried with Clonezilla already?
[http://clonezilla.org/](http://clonezilla.org/)

At work, we do a lot of HDD cloning and Ghost is well known by destroying GNU/Linux distro's boot loader (be it GRUB or LILO). Clonezilla does a good job, and it's just a small Live CD. Pretty nice alternative to commercial solution by Norton.

---

### Post by jamesisin on 2010-05-22
There is also Disc Copy (I think they are at version 2) which is another live CD option.

From your Ubuntu Live CD you could also use dd to make an image of the drive (or individual partitions).  See man dd for more information.

---

