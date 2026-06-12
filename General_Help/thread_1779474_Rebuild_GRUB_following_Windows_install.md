---
title: "Rebuild GRUB following Windows install"
date: 2011-06-10
forum: General Help
---

### Post by zcacogp on 2011-06-10
Chaps, 

OK, I'm struggling a little with something which I suspect is quite easy. 

I have a machine with a HDD with XP on the first partition, and 11.04 on the second one. All was working fine until I reinstalled XP. This, as expected, removed GRUB from the boot up sequence, making the machine boot straight into Windows each time. I'd quite like to get my Ubuntu option back, so I followed the instructions here: 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) 

... booting into a live session from the install disk. 

BUT, due to problems with grahics drivers on my machine (see here: 

[http://ubuntuforums.org/showthread.php?t=1776649](http://ubuntuforums.org/showthread.php?t=1776649) ) 

... my machine won't run from the live CD (once you have chosen 'Try Ubuntu', it plays the login sound, takes you to a black screen and won't do any more.) 

So I've been trying to make it work with the live CD from Lucid (10.10). And I can't make this work. I think I am having problems with the fact that the versions of GRUB are different between 10.10 and 11.04 - #grub-install -v tells me 

```
 grub-install (GNU GRUB 1.98-1ubuntu5)
```

Does this mean that I can't use a live CD from 10.10 to re-build grub for an 11.04 installation? 

If I *can* use this CD, then what do I type? If I put in ```
sudo grub-install --boot-directory=/media/<UUID HERE>/boot /dev/sdb2
```, then I get ```
Unrecognized option '--boot-directory=/media/<UUID HERE>/boot'
```

If I use the instructions for the earlier version of GRUB, and type ```
sudo grub-install --root-directory=/media/<UUID HERE> /dev/sdb2
```

... then I am told words to the effect of "Warning, Attempting to install GRUB to a partition instead of the MBR, this is a BAD idea. Warning, Embed is not possible, GRUB can only be setup using blocklists, but these are unreliable and not encouraged. If you really want to use blocklists then use --force."

Where do I go from here? The only option I can see is to re-install, but this seems to be a big hammer to smash a small nut. 

All help greatly welcomed - thanks. 


Oli.

P.S. When I put <UUID HERE>, I used the UUID from the Disk Utility application, and also used the Device list (/dev/sdb2) from there as well, for the partition which I know Ubuntu is loaded into.

---

### Post by oldfred on 2011-06-10
It is my understanding that the new grub 1.99 has enough changes that you really have to use the same LiveCD to reinstall grub2. 

If you cannot boot with the 11.04 liveCD then you may be able to chroot into your system to reinstall grub2 as then you are using the version in the install.

With liveCD have you tried the nomodeset or other options? Press any key, then f6 just as liveCD is starting.

To chroot.
You should not have to reinstall grub2, just install grub2's boot loader to the MBR.
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Once chrooted:
sudo grub-install /dev/sda

---

### Post by luca5am on 2011-06-10
Is there a safe mode in the live CD? If yes, have you tried it?

---

### Post by zcacogp on 2011-06-12
Oldfred, 

Thanks for your reply - that was ideal. Precisely what I was looking for. More particularly, the nomodeset boot option, which allowed me to use the "Try Ubuntu without installing" option without video card problems. So, very many thanks, that has allowed me to access the Ubuntu install, and to rebuild GRUB, and hence to set everything back to how it should be. 

Luca5am - Yes, a Safe Mode was pretty much what I was looking for, and the nomodeset was ideal. It's not a true 'Safe Mode', but it does seem to be a lower graphics mode, which worked for me. Thanks for your help. 

Thanks again chaps. I'm very grateful. I'll set this thread to 'Solved' (if I can work out how .... !) 


Oli.

---

