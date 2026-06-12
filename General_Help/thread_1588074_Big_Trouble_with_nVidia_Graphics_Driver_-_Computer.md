---
title: "Big Trouble with nVidia Graphics Driver - Computer Wrecked"
date: 2010-10-04
forum: General Help
---

### Post by steevven1 on 2010-10-04
I am very short on time right now, so I'll make sure to respond with more detail later, but basically, I'm running Ubuntu 10.04, and I have an nVidia GeForce 8400 graphics card. When I first installed it, I used Ubuntu's "System > Hardware Drivers" feature, and it worked great, but the graphics seemed just a tad slow.

Being a perfectionist, I went to nVidia's site and installed a beta driver to try it out; it was provided as a ".run" file.

After installing this, my computer will only run in "low-graphics mode," and, inexplicably, Aptitude and "System > Hardware Drivers" have stopped working entirely.

It seems like this graphics thing from nVidia has totally destroyed me. How can I revert?!

Thank you,
Steven

---

### Post by andrewthomas on 2010-10-04
Did you uninstall the drivers from System > Hardware Drivers before you installed the drivers from nVidia?

---

### Post by steevven1 on 2010-10-04
No, I did not. I suppose that wasn't a very good choice :-p  Any suggestions on options to remedy the situation? Thank you very much.

---

### Post by ellgor on 2010-10-05
Hi,

Read somewhere that the nvidia drivers don't get loaded in correctly, = problems, I found a couple of guides that gets them in and running, use whichever part helps:

** Do this at your own risk ( I have done this twice with no ill effects).

If you have a black screen give it a few minutes, try pressing  Ctrl-Alt-F1 (or any F upto 6) should this fail to give you a working environment (console) reboot and as soon as any text shows press the Tab key(keep it pressed) this should show a grub boot screen where you can choose to boot into a terminal, note this works most times. 

For those considering changing nvidia drivers, this little snippet prevents ending up with a black screen that does nothing:

Modify modprobe:
sudo gedit /etc/modprobe.d/blacklist-framebuffer.conf  

put a # in front of  blacklist vesafb and ADD blacklist vgafb16

Modify modules:
sudo gedit /etc/initramfs-tools/modules

Add fbcon and vesafb (after the vesa entry enter a blank line, close and save)

Update:
sudo update-initramfs -u

Modify grub:
sudo gedit /etc/default/grub

search for GRUB_CMDLINE_LINUX="" and ADD vga=771 or 795(first is better) between the quotes, then do:

sudo update-grub

**
Once the drivers have been loaded in you may need to change the vga=771 back to blank "", as it may affect the login screen.
**

1) Download latest driver from Nvidia site (that matches your card)

2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf

3) Add these lines and save: (might be a blank doc, adding these creates it now)

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*

5) Reboot your computer

6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)

7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have) be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

8) Follow the onscreen guide from Nvidia and when done
9) Start GDM

sudo service gdm start

---

### Post by bonixavier on 2010-10-05
Hi!

I spent the whole night trying, but I could figure out how to fix the same problem you're having trying to install the nvidia's website driver. Here's what you should do:
-Reboot your PC and start Ubuntu in recovery mode. If you don't dual boot, keep shift pressed after the BIOS screen.
-Choose the root option (it's the last one).
-Just to be sure (you don't want to be messing with your system as a super-user), write initel 3 and type your username and pw
-Go to the directory where you downloaded the .run file. If you haven't done it yet, type sudo sh NVI... -x. That will create a new directory with the same name as the file (except for the extension). Go into that directory and type (IIRC, check first the name of the command) sudo nvidia-installer -uninstall. If it's not in the first dir, it's in the kernel one.
-Now that you uninstalled the conflicting driver, reboot and start normally.
-Deactivate all the proprietary drivers. It won't work with them on. That will make your default driver become nouveau, which means that you're halfway there.

From now on, I'll take the liberty to quote myself:

> **bonixavier said:**
> This is what I did to finally get the driver to work (guess it may help others):
1- Do not install any proprietary drivers from the repository - they  will conflict with the driver you downloaded from nvidia's website.
2- Disable nouveau permanently. In a terminal, type:
```
echo options nouveau modeset=0 | sudo tee -a /etc/modprobe.d/nouveau-kms.conf
sudo update-initramfs -u
```*If you can't install the driver, or it  doesn't work, you'll have to restore the old xorg.conf file following  coffeecat's instructions (NOTE:click the arrow to see the original thread, it's the post right before this one). You'll just have to edit it to switch to nv  until you can get nouveau back.
3- Reboot and start in recovery mode.
4- Type telinit 3 then type your username and pw
5- Run the script you downloaded sudo sh NVIDIA..... and follow the instructions.
6- Startx then reboot just to see if it's working.

To me, it worked like a charm. Tell me if it's replicable.

---

