---
title: "unable to mount HD at boot."
date: 2010-10-14
forum: General Help
---

### Post by thedanomyte on 2010-10-14
All right... I've not been able to find anything quite like this before. It seems (really not sure what happened...) that my hp dv4 laptop failed to hibernate. when I came back, the fan was still spinning, the 'on' indicator was lit, opened the screen to find a black screen with a white cursor blinking.
 
the reboot halted when it failed to mount /dev, /sys and /proc. it gives me a comand shell named 'ash'. typing /init gives similar errors reporting that the device is busy. different from the first error that there 'is no such file...' 
 
booting off a live CD, the disk utility can't mount or otherwise manipulate the drive. the error comes back (again) that the device is busy. 
 
I'm looking for some way to get at the hard disk to either recover it or format the thing and start over. (backups are wonderful.) However, using the livecd to format fails as well.

---

### Post by TuxLyn on 2010-10-14
I would suggest using Gparted live cd to format the hard drive first, then try installing ubuntu again.

---

### Post by thedanomyte on 2010-10-14
done and done. gparted did the trick.

it came back with an error, though, but it's back to working... thank you for your help.

---

### Post by TuxLyn on 2010-10-14
Not a problem buddy. When I have similar issues with hard drives Gparted works great.

---

