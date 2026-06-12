---
title: "Boot Screen in Low Res with RGB lines"
date: 2010-09-05
forum: General Help
---

### Post by v0rtexza on 2010-09-05
Hey all,
I am new to ubuntu and have been using it for about a week now. Everything was going great, updated my nvidia drivers, did initial updates etc... And everything was awesome from the boot screen to the shutdown screen.
Recently (today) I installed a few updates that update manager thought were essential. However after doing so, when I restarted my computer and got to what should have been the boot screen, it simply sat for a few seconds with a few horizontal RGB lines and then booted to the login window... I have done nothing else to the pc besides those updates.
Also when I shutdown I get the same few RGB lines, they are in the top area of my monitor @ a 135 degree angle, if anyone has any idea what could be causing this. I would be very greatful, its not that a big deal but is rather annoying, I miss my ubuntu boot screen lol :)

---

### Post by v0rtexza on 2010-09-05
Fixed the issue. The below from [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) helped!
Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801")
One fix for this is to create this file.
 	Code:
 	gksu gedit /etc/initramfs-tools/conf.d/splash 
 and add this option FRAMEBUFFER=y, save the file.
Then
 	Code:
 	sudo update-initramfs -u 
Plymouth now has a hard dependency on mountall thus trying to  remove Plymouth would remove half the OS. The advice is, if you don't  want a graphical boot then uninstall any plymouth themes.
Thanks ubuntu forums, what would a ubuntu n00b do without ubuntu forums ;)

---

