---
title: "Loading a partion manually?"
date: 2010-08-02
forum: General Help
---

### Post by Codix121 on 2010-08-02
Messed up my grub and I'm wondering, is there anyway to manually boot a partition. My linux is on /dev/SDB3 how can I boot from it?

---

### Post by cj.surrusco on 2010-08-02
How exactly did you mess up your grub? If you are using grub 2 (the default since 9.10), then it will automatically add OS's. If that is that case, then you would want to boot into a live CD and recover Grub. It would help to know exactly how you messed Grub up.

---

### Post by Codix121 on 2010-08-02
Well i was trying to set it up so that only windows and linux showed since I have other random partions so in the grub menu I commented out (using ##) those that I didn't want, however, I only left the wrong partion of linux, when I boot it, it just goes to a black screen.... and now I can't get back to the correct partion to fix it :(

---

### Post by cj.surrusco on 2010-08-02
You probably edited the /boot/grub/grub.cfg, which you aren't supposed to edit at all. There are other ways of getting rid of entries that don't belong there. 

What you want to do to fix this is boot into a live cd and edit the grub.cfg and remove the comment symbols. 

When you get into the live CD, mount your Ubuntu partition, then open a root nautilus. 
```
gksudo nautilus
```
Then navigate to /boot/grub/grub.cfg (in the mounted partition for Ubuntu, NOT the live CD filesystem) and open it.
Remove the comment symbols and save it.

Update the bootloader:
```
sudo grub-install --root-directory=MOUNTPOINT /dev/sdX
```
The "--root-directory" would be where you mounted your Ubuntu partition, for example /media/Ubuntu.

/dev/sdX would be the hard drive that Ubuntu is installed on, which is most likely /dev/sda if you only have one hard drive.

Cross your fingers and reboot.

---

### Post by Codix121 on 2010-08-02
I'm on a live cd but apparently there is no grub menu... I did what you did but couldn't navigate to the boot menu, it just says DESKTOP.. I've tried everyway to edit the grub but I can't find a way :( Correct me if I'm wrong am I suppose to boot the live CD and run "try ubuntu without installing" I've also tried the boot menu and going to "EDIT" and it allows me to edit the command that I'm booting but I can't seem to get the combination right (HD1, 2) anyway of How I can figure out which partion it is.. it would be greatly appreciated..

---

