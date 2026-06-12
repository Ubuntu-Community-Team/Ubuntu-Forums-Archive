---
title: "Grub Rescue after Installing Lubuntu to a USB drive"
date: 2011-01-10
forum: General Help
---

### Post by MrJLBrown on 2011-01-10
I tell you, I really am a sucker for linux distros that can fit on a flash drive. Problem is that installing Lubuntu to a USB gives me more headaches than Puppy originally did.

After I installed Lubuntu to a USB drive, I rebooted to see if I had done anything to how my hard drive boots Ubuntu.

It did.

I get a seemingly worthless grub rescue prompt where it seems no command is recognized. What I can do, though, is pop my Lubuntu USB back in and can choose from grub to boot from my hard drive. From that I deduce a few things. 1). My grub on my hard drive is spinning it's wheels because it's looking for something that isn't there, but is there on the flash drive. 2). The MBR on my primary partition has been overwritten so that it thinks that grub should run only on the USB's volume. 3) Some contingency I can't identify is what's causing my headaches.

It's really only a minor inconvenience for now, since I have to have the USB drive at hand every time I boot the computer which would render me screwed if I lost the darn thing.

I've heard of using a live disc to restore grub, but when I type sudo grub it says that grub is not installed. Is that normal? I'm really out of my element, here.

---

### Post by C.S.Cameron on 2011-01-11
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by MrJLBrown on 2011-01-11
Thank you so much! That worked perfectly--I'll definitely remember that next time I have grub issues.

---

