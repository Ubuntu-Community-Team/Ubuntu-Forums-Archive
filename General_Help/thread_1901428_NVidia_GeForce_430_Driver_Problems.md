---
title: "NVidia GeForce 430 Driver Problems"
date: 2011-12-28
forum: General Help
---

### Post by shadomastr on 2011-12-28
Hi folks, 

I've spent a good amount of time browsing these forums as of late, but haven't found anyone with similar symptoms or a solution. 

I built a computer yesterday on the cheap and used an NVidia GeForce 430 graphics card. Ubuntu installed fine and fell back onto Unity 2D. I went to update my drivers, and had two options. I could do the standard NVidia drivers or the updated NVidia drivers, both of which were "certified by Ubuntu/Canonical." When I reboot after updating the drivers, my computer freezes on a blown up image of the Ubuntu screen with 4/5 red dots (image attached) and will not boot into Unity.

I have 2 questions:

1. How can I enter safe mode/recovery mode from this screen and use a terminal. I know the commands to remove the drivers, but I can't access a terminal.

2. Can this problem be fixed? If I can't even use my graphics card I would prefer to exchange it for one that works. However, the graphics card is certified to work with Ubuntu, so I suspect there is a fix. 

Thanks in advance

P.S. I'm running 64 bit Ubuntu 11.10 Oneiric Ocelot

---

### Post by Bobhuber on 2011-12-28
When you install Ubuntu put a checkmark next to install 3rd party drivers and it will automatically install the correct drivers for the card. If you want to install the latest Nvidia drivers after the install use the 285.05.09 drivers from their  website and not the newest 290.--- drivers. The card works great in Ubuntu so you may have other problems if that doesn't work.

---

### Post by shadomastr on 2011-12-28
> **Bobhuber said:**
>  If you want to install the latest Nvidia drivers after the install use the 285.05.09 drivers from their  website and not the newest 290.--- drivers.

First, thanks so much for your help! 

I ran the command 

```
sudo sh NVIDIA-Linux-x86_64-285.05.09.run
```

and received an error box saying

```
You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at www.nvidia.com.
```

I went to the README and found a short paragraph  that says
  **When I try to install the driver, the installer claims that X is running, even though I have exited X.**
    
 The installer detects the presence of an X server by checking for the X server's lock files: /tmp/.Xn-lock, where 'n' is the number of the X Display (the installer checks for X Displays 0-7). If you have exited X, but one of these files has been left behind, then you will need to manually delete the lock file. *Do not* remove this file if X is still running!


I don't know what server X is. Can  you point me in the right direction?

---

### Post by Baconator507 on 2011-12-28
you need to shutdown the X server.

press ctrl+alt+F1
type sudo service gdm stop

then try to run installer from that terminal

---

### Post by shadomastr on 2011-12-28
> **Baconator507 said:**
> you need to shutdown the X server.

press ctrl+alt+F1
type sudo service gdm stop

then try to run installer from that terminal

terminal says ```
gdm: unrecognized service
```

ctrl+alt+F1 doesn't work either. I believe I read in another forum that gdm is not recognized in 11.10, but I could be mistaken.

---

### Post by Baconator507 on 2011-12-28
OK... try this:

sudo service lightdm stop

---

### Post by shadomastr on 2011-12-28
> **Baconator507 said:**
> OK... try this:

sudo service lightdm stop

Okay. That definitely did something. I have a black screen, no GUI and I can type, but when I press enter the commands aren't executed.

---

### Post by shadomastr on 2011-12-28
Okay. I found this, which talks about installation of the driver

[http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/290.10/README/installdriver.html)

I also found this, which I think may help. Basically, the X server is getting started after I install the NVIDIA drivers from the system settings, and it was causing the freezing at the splash screen

On most distributions, the default runlevel is stored in the file /etc/inittab, although you may have to consult the guide for your own distribution. The line that indicates the default runlevel appears as
     id:n:initdefault:  or similar, where n indicates the number of the runlevel. /etc/inittab must be edited as root. Please read the sections on editing files and root user if you are unfamiliar with this concept. Also, it is recommended that you create a copy of the file prior to editing it, particularly if you are new to Linux text editors, in case you accidentally corrupt the file:
     # cp /etc/inittab /etc/inittab.original  The line should be edited such that an appropriate runlevel is the default (1, 2, or 3 on most systems):
     id:3:initdefault:  After saving the changes, exit X. After the Driver installation is complete, you may revert the default runlevel to its original state, either by editing the /etc/inittab again or by moving your backup copy back to its original name.
 Different distributions provide different ways to exit X. On many systems, the init utility will change the current runlevel. This can be used to change to a runlevel in which X is not running.
     # init 3  There are other methods by which to exit X. Please consult your distribution.

Now, I looked ifor an /etc/inittab file, but I couldn't find one to edit. Does anyone know where it would be?

---

### Post by Bobhuber on 2011-12-28
Lets fix one thing at a time and then we will install the drivers.Were going to fix the prompt (or lack of) problem first by using uvesafb during boot and VT.Follow carefully.
From a terminal do the following >
sudo apt-get install v86d
echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
sudo cp /etc/default/grub /etc/default/grub-backup
Edit the grub file and change 2 lines and save the file >
gksu gedit /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap"

GRUB_GFXMODE=1280x1024
----------------------------------------------
Edit this file and save after adding the line at the end>
gksu gedit /etc/initramfs-tools/modules
ADD this to the bottom of the file >
uvesafb mode_option=1280x1024-24 mtrr=3 scroll=ywrap
-------------------------------------------------------
Almost done >
sudo update-grub
sudo update-initramfs -u
REBOOT the computer
Ctrl+Alt+F1 should now give you a prompt in the terminal that you can see
Login with your password
sudo stop lightdm
Change to the directory with the  NVIDIA-Linux-x86_64-285.05.09.run   (cd /home/bob/Downloads)
sudo sh ./NVIDIA-Linux-x86_64-285.05.09.run

---

