---
title: "Managing GRUB between two seperate installs of Ubuntu"
date: 2011-08-11
forum: General Help
---

### Post by diablo75 on 2011-08-11
I have a client who asked me to setup two seperate installations of Ubuntu on his system for him; the intention being that he would have a fall back strategy in the event he screwed something up with the primary install.  We have two seperate partitions set aside for each respective distro's / (root) and a large partition that both OS's mount as /home.

Thinking about this just now I have a feeling that what I should have done was added one more tiny partition to house /boot for both OS's.  Would that have been the best thing to do?

What is happening right now is both / partitions have a /boot folder and the MBR is mounting the secondary /boot folder (from Ubuntu #2) to run GRUB at the startup.  The menu list of this /boot folder is giving priority to the instance of Ubuntu we had intended to function as the backup because the size of it's partition is much smaller.

Well anyway, I'm going to guess the best way to fix this is to have a /boot partition that both OSs can share, but I don't know how to change the current configuration for both systems to do that.

---

### Post by ~!geek!~ on 2011-08-11
Indeed having a committed /boot partition for all the instances of ubuntu is a good thing to do.
But the problem you mentioned here is not that tough to solve. 
Every ubuntu installation runs update-grub command at the end of installation and thus writing mbr each time.

You may use some software to manage grub list and having previously installed ubuntu as the default selection. Google something to configure grub list etc. Sorry for not searching it for you. It shudn't be tough though.

---

### Post by diablo75 on 2011-08-11
> **~!geek!~ said:**
> Indeed having a committed /boot partition for all the instances of ubuntu is a good thing to do.
But the problem you mentioned here is not that tough to solve. 
Every ubuntu installation runs update-grub command at the end of installation and thus writing mbr each time.

You may use some software to manage grub list and having previously installed ubuntu as the default selection. Google something to configure grub list etc. Sorry for not searching it for you. It shudn't be tough though.

I don't think you are correct about update-grub rewritting the MBR because I ran it manually from the instance of Ubuntu whose grub installation was not being accessed by the MBR and after running it the exact same (unwanted, secondary) grub menu remained.  You can also tell that you are editing the wrong grub menu when running the primary copy of Ubuntu because the second instance of Ubuntu listed in the menu says "on /dev/sda7" after the kernel version.  Likewise, when you edit the grub (that is being booted from) while running the secondary Ubuntu the secondary entries for Ubuntu say "on /dev/sda1".

So I think what might be best at this point is to try and find a way to consolidate the /boot on both installations into a new, separate /boot partition that each OS share.

---

### Post by drs305 on 2011-08-11
If yo mean putting both OS's into the same /boot folder it can lead to problems, especially if they are both Ubuntu. You'd be mixing initrd's, etc.

You can change control over to the OS you wish to control G2 by booting into that OS and running (change X to the drive name (sd**a**, sd**b**, etc). Do not include the partition number in the command:
```
sudo grub-install /dev/sdX
```

Note that from time to time an upgrade to the Grub packages may try to transfer control to the other Ubuntu installation. You can prevent that if desired by 'locking' the Grub 2 package versions (grub-common, grub-pc) on the secondary OS. Or you can just run the above command again if it starts booting the wrong one.

---

### Post by haresear on 2011-08-11
I'm not sure that having a common /boot partition really solves your problem, because then both installs will be over-writing the same grub.cfg file that controls the menu list (assuming you are using grub2). Whichever install executes update-grub last will take control of the grub menu, and list its own install first. Control of the grub menu will be flipping back and forth as the two installs are updated.

Having a common /home might create similar problems if the two installs have the same user.

---

### Post by grahammechanical on 2011-08-11
I have three installations of Ubuntu on my disk. Unbuntu 11.04, Ubuntu Studio 11.04 and Ubuntu 11.10 alpha. I do not use a boot partition. I have found that the last installed Ubuntu will put its own grub menu into the MBR or where ever (I have no wish to argue about it). It will also put its own kernel at the top of the menu. Also every time there is a kernel update the last updated kernel will appear at the top of the menu.

The solution I found was to install Grub Customizer. It is in the Software Center. I would recommend this utility. It will let you set the boot order and keep the kernel (Ubuntu) that you want at the top of the list.

When my recent installation of 11.10 alpha 2 changed the grub menu, I simply booted into my Ubuntu 11.04 and ran Grub Customizer. I used Save and a file menu option to put Grub into the MBR and my Grub menu was back to the way I like it complete with the background image that I used Grub Customizer to fix for me.

Here is a link - book mark it

[http://ubuntuforums.org/showthread.php?p=10340183]("http://ubuntuforums.org/showthread.php?p=10340183")

Regards.

---

