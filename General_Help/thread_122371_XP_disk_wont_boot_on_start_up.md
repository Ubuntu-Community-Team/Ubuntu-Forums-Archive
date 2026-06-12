---
title: "XP disk wont boot on start up"
date: 2006-01-27
forum: General Help
---

### Post by angeleyes on 2006-01-27
How do I get my Windows XP disk to boot on startup so I can repair my Windows program so it will run?I need to reinstall missing boot file(it disappeared after I put Ubuntu in)so my XP will run.My husband and kids like Windows better then Ubuntu so I also am trying to find help on creating a dual boot system(I like Ubuntu)
I apprecaite any advice and I help I recieve.

---

### Post by Toxicity on 2006-01-27
I know that XPs installation cd has a a recovery console. As for how to actually use it I have no clue as I don't really play with XP as much as I should. The easiest Possible way to dual boot is formatting the hardrive, installign XP on a partition (make a partition through the Ubtunu install disks partion manager, if you're patient you can just let it install (but youll be installing it again later this way anyway)) With the desired free space available you could then install XP as it's a real How when it comes down to it, it domineers all free space. Basically thats the idea, you format entirely, create a partition of half or whatever of your harddrive for Ubuntu. Install XP on that free space then run back and install Ubuntu on the partition (make sure when doing this you leave space for swap and all of that. Like I said this is a pretty sucky option. Your best bet if you have no way to backup your HDD is reading up on the XP install disks restore console I'm pretty sure you can perform file checks there.... I have also before installed XP Over an old XP installation which saves all files non system specific. It bones the registry to hell though as its wiped to the basics meaning some programs will have difficulty running until you reinstall them. But still you lose minimal data. Whats going to happen if you install ubuntu after XP (You've probably done it all ready assuming so from the post but just to be safe) if you'll be prompted about the GRUB loader, allow it to install and after that it will be the first thing you see after BIOS loading. The thing is Windows hogs the boot sector, that being why you should install Windows Then Ubuntu. Unless your experienced with this sort of thing.

---

### Post by nikosft on 2006-01-27
Boot with your winxp cd. In the prompt screen choose repair. Choose your installation and in the command prompt write 

fixmbr

which stands for fix master boot record. I think it may help

---

