---
title: "CD loading trouble"
date: 2006-04-23
forum: General Help
---

### Post by JoeeT on 2006-04-23
Hi there. I am trying to install the 64 version of Ubuntu, but have trouble when the installer attempts to load components from CD, but I get the error stating that
 
"There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM."

I have used an official Ubuntu disc, 1 which I burnt andone which a friend burnt, and no luck so far there.
I found a work-around for 32 bit which involves doing something for 'hdparm': a solution found in [this thread]("http://www.ubuntuforums.org/showthread.php?t=81600&page=2&highlight=CD-ROM+integrity"), but this cannot be done in the 64 installation.

Another thread I found said that the following would work:

> 
Boot with expert mode. Step through, but BEFORE "Detect and mount
CD-ROM", switch to console with Alt-F2, and enter these two commands:
umount /cdrom
mount /dev/cdroms/cdrom0 /cdrom
Switch back with Alt-F1, and continue installation.


I attempt to follow these instructions. However, when I attempt 'umount /cdrom' I recieve an error to state that there is no such file or directory as '/cdrom'.

What is it that I am doing wrong? And are there any other solutions to the CD-ROM problem that DONT involve re-burning at a slower speed (as I hear this doesnt always solve the problem and I have had no luck doing it so far).

Thanks in advance.

---

