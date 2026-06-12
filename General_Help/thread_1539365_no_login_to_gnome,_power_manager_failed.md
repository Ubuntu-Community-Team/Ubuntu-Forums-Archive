---
title: "no login to gnome, power manager failed"
date: 2010-07-26
forum: General Help
---

### Post by anthonie on 2010-07-26
System: 	Ubuntu 9.10, upgraded from previous versions
Architecture:	64 bit
Filesystem:	EXT4
DE:		Gnome

Occurance of the problem: After using GParted to move unallocated space to a ntfs-filesystem.

Yep. I did it again. No oops this time, for I have no clue why this error appeared and why I cant get to my desktop. No recent updates that couldve borked the system.

Lately I have had to work quite a bit with some Windows-only programs, and I found myself out of harddisk space pretty soon, as for the last year or two, I worked almost exclusively with Ubuntu and only had a minimally sized partition set up for Windows. I needed room. No problem, I thought, I will start up GParted, move some of the unallocated space to the NTFS partition and be done with it.

I have performed tasks like that before, so no problem should occur.  

I thought...

Description of the problem.
--------------------------------------
After rebooting I got to the grub menu. All options were there. Looks nice. Except for the fact that Windows did not want to start, some MSDK (sorry, did not write down the name) file or whatever was missing. (I heard this is a Vista problem and the file connected to the error does not even exist on any XP system).

Worse than XP not starting was the error message I got from my login screen.
It told me:

"The configuration defaults for gnome-power-manager have not been loaded. Please contact your administrator."

So I did. I talked to myself and had to admit to the user that I did not have a solution at hand. User upset, administrator too. (They are no longer talking to each other.)

Login is accepted, but after that nothing. Just a black screen with a mouse-pointer that can be moved around. Nada mas. 

One other thing:

Before getting to the login screen, there was something else that drew my attention, but again, I did not know what it meant. 

The error-message:

fsck from util-linux-ng 2.16 is udevd [527]: NAME: "%k" is superfluous and breaks kernel supplied names, please move it from /etc/udev/rules.d/51-hso-udev.rules:124

* stopping the Firestarter firewall...
9.10: clean, 467963/3055616 files, 8323370/12205383 blocks
[     23.541016] ACPI: I/O resource nForce2_mbus [x4c00-0x4e3f] conflicts with CPI region SM00 [0x4c00-0x4e3f]
[     23.541084] nForce2_mbus 0000:00:03.2: Error probing SMB2.
* Setting preliminary keymap
* Starting AppArmor profiles


Things I tried
-------------------
Safe-mode. Of course. Result: Same problem.

SuperGrub. It allowed me to boot, but thats it. No further steps taken, if only because SuperGrub does not support the EXT4 filesystem (yet?).

I have heard people were able to get to their desktop after receiving this error by using a root account they had previously created. I dont have one, so that would not work.

So, I did the three finger salute, stopped the gdm from the terminal, moved gconfd to somewhere else, hoping a new file would be created and the problem would be solved with that, but no. Restarted gdm, it worked but the problem remained. 

Ok. Perhaps a reinstall of the GDM might work, I thought. Well, it might, but the problem is I have no internet connection and the usual way I connect my laptop is through phone-tethering. Not having a desktop will not allow me to make a connection.

So, sudo apt-get --reinstall install gnome-power-manager did not work as an active connection is required. Also I dont know if that is going to solve the problem.

So now I am in the dark. I have booted up a live CD, mounted my HD partition in order to check my /root/.Xauthority, but I could not even find the file.

So, what now?
---------------------
I refuse to believe there is a serious problem with my Ubuntu install. As far as I can see, there is a problem with some config-files but the system itself looks OK. Reinstalling is preferably not an option, as I love my install and have been working with it for a long time now, with lots of user data on it as well. Also, I have not seperated /HOME, which makes a reinstall a bit of a drag. I am certain there is an easy fix somewhere, someway, but I would need some advice from someone more knowledgable than I am. 

The only thing I could think of is to find a way to reinstall gnome-power-manager without an active connection. I can download the .deb file with some other device than my laptop but I would not know how to add that to /etc/apt/sources.list. Also, I kind of doubt that the problem lies within a faulty power-manager.

Pointers, papers to read or just a straight out solution, I welcome it all :D

regards,
Anthonie

---

### Post by anthonie on 2010-07-29
Bump.

No one? Or am I missing something obvious here and has the problem been solved one way or another?

---

### Post by DjSesso on 2010-08-12
I get the same problem on a new install.

---

