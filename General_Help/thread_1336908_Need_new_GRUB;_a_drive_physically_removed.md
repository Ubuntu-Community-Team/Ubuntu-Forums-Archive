---
title: "Need new GRUB; a drive physically removed"
date: 2009-11-25
forum: General Help
---

### Post by Ubunthree on 2009-11-25
If this has already been dealt with in an existing thread, please point me to it; I didn't find anything with the searching that I did.

I have two hard drives; one with Windows XP and one with two Ubuntu installations (I leapfrog them over each other as new versions come out).

I was curious to know how Ubuntu (Jaunty) would work if I actually installed it onto a USB flash drive, not as a live-CD type of thing but as an actual installation. So I plugged in an 8GB thumb drive, booted up as a live-CD user and ran the installation onto the thumb drive. Everything went as if I were installing normally onto a hard drive, and the new installation seemed to work fine, though quite sluggishly as one would expect. Curiosity satisfied, and having no other use for the new installation, I pulled the thumb drive and started using it for other things, not realizing until too late that GRUB would now be looking for three drives at boot, and would be missing the one which I had removed and effectively destroyed.

So of course now I am unable to boot anything other than a live CD. I can use my laptop to access either of the hard drives through a USB converter cable, and I can edit config files that way. I assume, though, that the relevant GRUB menu.lst file would be the one which no longer exists, and I don't know nearly enough to do whatever I need to do to restore my boot routine.

I've never messed with GRUB beyond simply changing the default boot pointer and timeout settings. Is there a way to boot the live CD, get into GRUB somehow, and tell it to look at an existing menu.lst instead of the one which is now gone?

Thanks!

---

### Post by Ubunthree on 2009-11-25
I guess I have solved this for myself by reinstalling Jaunty into the old Intrepid partition, which rebuilt GRUB in the process. So I no longer need an answer to this, but I'm still kind of interested in knowing whether there was another way or not.

---

