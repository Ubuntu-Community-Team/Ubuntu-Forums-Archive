---
title: "problems mounting a data CD in Ubuntu 10.10"
date: 2011-01-20
forum: General Help
---

### Post by xsilentmurmurx on 2011-01-20
Hey there everyone I am new to the forums but not totally new to Linux. So here is the deal: On Sunday, I installed Ubuntu 10.10 on my friend's laptop as his primary OS. All went well, but he is attempting to access a data cd that he inserted into the cdrom drive and is having some trouble doing it. For some strange reason, Ubuntu does not automatically mount the cdrom drive as soon as a cd is inserted into the drive. I had him do :

sudo mkdir /media/cdrom
sudo mount -t iso9660 /dev/cdrom /media/cdrom

and it gave him a wrong fs type error

then i had him do: sudo mount /dev/cdrom /media/cdrom which gave an error as well. 

Then I had him do sudo mount /dev/cdrom /media/cdrom -o unhide
and that gave him an error message that says: mount: /dev/sr0: unknown device

does anyone have any idea how I can resolve this and also how to set up his system so it will automatically mount a cd when it is inserted into the drive?

---

