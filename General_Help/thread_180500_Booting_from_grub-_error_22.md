---
title: "Booting from grub- error 22"
date: 2006-05-22
forum: General Help
---

### Post by pedstunite on 2006-05-22
Hi,

I have attempted to follow a set of online directions in order to get a dual booting ubuntu/windows system.
[http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#installbreezy](http://www.hezardastan.org/breezy_xp_dualboot/en/breezyinstall.html#installbreezy)

I have followed the instructions exactly.  I previously tried out the live cd to make sure everything worked ok.  Had to make some changes to make my video card work, but I was able to get past the gtparted phase using the live cd, then, using the install cd, I did the expert install.  I followed your directions for setting up the partitions.  The only difference is that I have a sda drive, not a hda drive.  So, instead of having the grub loader on /dev/hda3, I put in /dev/sda3.

So, when I reboot, I get the grub loader, and can choose between ubuntu and windows.  However, when I make my choice, windows or ubuntu, I get

root (hd1, 2)

Error 21:  Selected disk does not exist

Does anyone have any suggestions?

Thanks alot

pedstunite

---

### Post by themadhatter0 on 2006-05-22
Hmm...sda is usually used for external drives (i.e. usb or firewire hard discs). Do you have such a drive? I have never tried installing grub on an external drive, but I can imagine it might cause problems since the USB and FireWire drivers won't be installed until later in the boot process. Has anyone else tried installing their boot loader on an external drive? I'm sure it is possible but I don't know how!

In the mean time, you can repair your Windows partition by inserting the windows CD, starting the repair console (press 'r' when you get to the first selection screen) and typing 'fixboot' followed by 'fixmbr' at the command prompt. That will restore the Windows boot loader but will not help you get into Ubuntu I'm afraid!

---

### Post by pedstunite on 2006-05-22
[QUOTE=themadhatter0]Hmm...sda is usually used for external drives (i.e. usb or firewire hard discs). Do you have such a drive? I have never tried installing grub on an external drive, but I can imagine it might cause problems since the USB and FireWire drivers won't be installed until later in the boot process. Has anyone else tried installing their boot loader on an external drive? I'm sure it is possible but I don't know how!

In the mean time, you can repair your Windows partition by inserting the windows CD, starting the repair console (press 'r' when you get to the first selection screen) and typing 'fixboot' followed by 'fixmbr' at the command prompt. That will restore the Windows boot loader but will not help you get into Ubuntu I'm afraid![/QUOTE]
The drive that I have is an SATA drive.  Its a new computer that I set up and installed windows on myself.  Maybe I have that hard drive set up the wrong way?  Using the live CD and running gtparted, I can see that all the drives are set up as sda

---

### Post by pedstunite on 2006-05-22
[QUOTE=pedstunite]The drive that I have is an SATA drive.  Its a new computer that I set up and installed windows on myself.  Maybe I have that hard drive set up the wrong way?  Using the live CD and running gtparted, I can see that all the drives are set up as sda[/QUOTE]

I did the following now... as per [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

loaded grub, pressed c

1) root (hd0,2)

2) kernel /vmlinuz root=/dev/sda3

3) initrd /boot/initrd.img-2.6.12-9-386

4)boot


....and the installation of ubuntu continued!!!
I'll let you guys know what happens next.  This is fun!!

---

### Post by pedstunite on 2006-05-22
so now the installation stalled due to the lack of the video driver.  Before, I had this problem with the live CD, so I used expert install, and chose vesa instead of autodetect.  I don't see the option now when performing the real installation. 

Once the installation stops, could I just write the following as found in thread
[http://ubuntuforums.org/showthread.php?t=161995&highlight=ubuntu+install](http://ubuntuforums.org/showthread.php?t=161995&highlight=ubuntu+install)
+graphics+expert:

""After installing ubuntu I got the error 'Failed to start the X Server' etc and so I try to run:

"sudo dpkg-reconfigure xserver-xorg"

to set up the vesa thing but i get the error message "unable to lookup ubuntu in gethostbyname()" and I have no clue what this means.

Any help would be appreciated ... I was thinking I should just reinstall but If I don't have to that would be good ...

Also I had the same error with x-server when running the live cd but i got around it by running it in expert mode and stopping it from auto-detecting the video hardware, and telling it to use the nv drivers (or vesa) ... but when installing in expert mode no such option to disable auto-detection of video hardware came up, so yeah.""

[QUOTE=pedstunite]I did the following now... as per [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

loaded grub, pressed c

1) root (hd0,2)

2) kernel /vmlinuz root=/dev/sda3

3) initrd /boot/initrd.img-2.6.12-9-386

4)boot


....and the installation of ubuntu continued!!!
I'll let you guys know what happens next.  This is fun!![/QUOTE]

---

### Post by themadhatter0 on 2006-05-28
[QUOTE=pedstunite]
to set up the vesa thing but i get the error message "unable to lookup ubuntu in gethostbyname()" and I have no clue what this means.
[/QUOTE]

'gethostbyname()' is the DNS lookup function i.e. the function used to get an IP address given a URL. It looks like the installation is trying to connect to the Internet to get the new xserver-xorg package but either your network drivers aren't installed yet or they aren't configured yet.

There must be a way to force dpkg-reconfigure to get the needed files from the installation CD rather than from the net but I don't know what it is!

---

### Post by pedstunite on 2006-06-02
well, got it to work with the vesa drivers.  Just tried it again...

---

