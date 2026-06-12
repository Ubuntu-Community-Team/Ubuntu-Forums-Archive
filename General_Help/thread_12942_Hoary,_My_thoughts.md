---
title: "Hoary, My thoughts"
date: 2005-01-27
forum: General Help
---

### Post by AMP on 2005-01-27
I recently Downloaded the Hoary live cd, an Upgrade from my Warty disk which i sadly lost.
Now i have a  problem with the new disk
1 it did not mount my 2 HDD'S!!! Which totaly turned me off of it and made me re dl the old Live cd.
Other than that is is pretty much the same, except there is a new menu to choose from, also another thing i didnt like, it looked out of place.

Those are my thoughts.

---

### Post by oracledarren on 2005-01-27
I think that the auto mounting of the hdd's is more of a general security thing.

The original idea of a live cd was for people to try out an o/s or distro without it interefering with what you already had.

If you need to mount one though it is not a hugh task, just make a folder on the desktop goto a termnal and

mount -ro /dev/hda1 /pathtofolderondesktop and it is done.

obviously replace hda1 with what ever device is you hard drive and change the ro to rw if you want to write to the drive.

Hope this helps  :) 

Darren

---

### Post by Roberto Rosselli on 2005-01-28
[QUOTE=oracledarren]I think that the auto mounting of the hdd's is more of a general security thing.

The original idea of a live cd was for people to try out an o/s or distro without it interefering with what you already had.

If you need to mount one though it is not a hugh task, just make a folder on the desktop goto a termnal and

mount -ro /dev/hda1 /pathtofolderondesktop and it is done.

obviously replace hda1 with what ever device is you hard drive and change the ro to rw if you want to write to the drive.

Hope this helps  :) 

Darren[/QUOTE]
 Sorry, but I agree with the previous poster: having all your disk partitions mounted and easily accessible is a very nice feature, and one of the things I appreciate in Knoppix. If security concerns are so important, just mount them ro and ask the user if he wants them mounted as rw (with all the warning words you deem appropriate) the first time he tries to write on them.

Another things I think Knoppix gets right, is the easy and accessible way to "seed" a home directory in one of your partitions, be it fixed or removable. Is this possible in Ubuntu Live CD?
(still downloading it ...)

Ciao

---

