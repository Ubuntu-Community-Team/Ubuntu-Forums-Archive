---
title: "Ubuntu no longer boots"
date: 2011-06-14
forum: General Help
---

### Post by Fasih on 2011-06-14
Ok so I've been running Ubuntu for only a few days, and I was trying to get the Unity working (common error of the graphics card not being enabled)
One fix that I found on a site was to do ```
sudo apt-get install nvidia-173
```Once I did that, Ubuntu won't reboot. It goes through those lines, and one thing fails, which is something called system reporting or something like that, and it just stalls. I've looked everwhere and I can't figure out what to do.

I tried ```
sudo get-apt remove nvidia-173
```It removed it, but i still get the same error. What should I do? i can only boot in safe mode :S

Thanks in advance!

EDIT: My graphics card is a NVIDIA GEFORCE GT 525M

---

### Post by Quackers on 2011-06-14
Welcome to UF.
Boot into safe mode and run Additional Drivers (or Additional Hardware in older versions of Ubuntu) and install the Nvidia (recommended) driver for your card.

---

### Post by Fasih on 2011-06-14
Thanks for the reply. When I boot into safe mode (note I am dual booting Windows 7 and Ubuntu) I get a box that lists several options, but it only allows me to type commands.

---

### Post by Quackers on 2011-06-14
Are you getting a grub menu to choose which OS to boot?

---

### Post by Fasih on 2011-06-14
Yeah. I can choose normal ubuntu, the safe more version and Win7

---

### Post by oldfred on 2011-06-14
I have in my notes this procedure, but it was a version or two ago.

Boot to command line video issues
Remove nvidia drivers -> install nouveau -> reboot and let Ubuntu detect your videocard when you're running the desktop -> install the new drivers -> reboot.
#Remove nvidia
sudo apt-get purge nvidia-common
#Install nouveau and remove the xorg.conf
sudo apt-get install xserver-xorg-video-nouveau
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
#Make sure you undo the changes you made in /etc/default/grub
sudo nano /etc/default/grub
#Restore the line GRUB_CMDLINE... to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
sudo update-grub
Reboot

I find I cannot boot with nouveau unless I add nomodeset. I have a nVidia 9600GT.
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
Then you should be able to choose the correct current version nVidia driver. I think the 173 was just for the very old nVidia cards. 
How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

From nVidia on current driver:
Please note: This NVIDIA Linux graphics driver release supports GeForce 6xxx and newer NVIDIA GPUs, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.

---

### Post by Quackers on 2011-06-14
Do you get the normal version as an option as well?
If so at the grub menu make sure the top entry is highlighted (should be Ubuntu normal) end press the "e" key. 
A new screen with text will appear.
Use the arrow keys to go to the end of the line that ends with "quiet splash" then leave a space after quiet splash then type in nomodeset then press ctrl + x to boot.
If it boots open up synaptic package manager and in the search box enter nvidia then everything to do with nvidia will appear in the main screen.
Anything nvidia that has a green box to its left uninstall it (right-click and select mark for removal). Then click on the green tick in the toolbar to apply the change.
Then reboot and see if it boots normally.
If it does run Additional Drivers and install the nvidia (recommended) one.

Or see oldfred's post above :-)

---

### Post by Fasih on 2011-06-15
> **Quackers said:**
> Do you get the normal version as an option as well?
If so at the grub menu make sure the top entry is highlighted (should be Ubuntu normal) end press the "e" key. 
A new screen with text will appear.
Use the arrow keys to go to the end of the line that ends with "quiet splash" then leave a space after quiet splash then type in nomodeset then press ctrl + x to boot.
If it boots open up synaptic package manager and in the search box enter nvidia then everything to do with nvidia will appear in the main screen.
Anything nvidia that has a green box to its left uninstall it (right-click and select mark for removal). Then click on the green tick in the toolbar to apply the change.
Then reboot and see if it boots normally.
If it does run Additional Drivers and install the nvidia (recommended) one.

Or see oldfred's post above :-)
I tried that and it just goes to a screen with text. I can log in using my username and password, and it acts like the terminal, but i cant download packages or anything. It won't connect or load.

---

### Post by Quackers on 2011-06-15
Have you tried oldfred's commands from that login you have?

---

### Post by Fasih on 2011-06-15
> **Quackers said:**
> Have you tried oldfred's commands from that login you have?

Well, I don't quite understand much of it. I'm completely new to the Linux scene. If you could explain what I must do I'd appreciate that

---

### Post by Quackers on 2011-06-15
From that text login you described run these commands one at a time. Make a note of any output.

sudo apt-get purge nvidia-common

sudo apt-get install xserver-xorg-video-nouveau  
   not sure whether that one will do anything without internet.

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

sudo reboot

then see if it boots.
If it goes to a black screen try adding nomodeset option as you did earlier to the grub menu entry.

---

### Post by Fasih on 2011-06-15
Thank you both so much! Problem solved. I'm back on Ubuntu. What a great feeling that it's working again. :)

Thanks again!

---

### Post by Quackers on 2011-06-15
Excellent :-)
oldfred saves the day....again :-)
It's worth checking that nothing nvidia related is still installed (via synaptic package manager) then you can run Additional Drivers from the menu and install the nvidia (recommended) driver, if you still want to :-)

---

### Post by Fasih on 2011-06-15
Yes thanks! That helped! Now Unix works and any application that gave me an openGL error works now!

---

### Post by Quackers on 2011-06-15
Very nice :-)
Please mark the thread as solved using Thread Tools near the top of the page. Thanks.
Happy Ubuntuing :-)

---

