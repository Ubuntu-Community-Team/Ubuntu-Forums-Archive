---
title: "How to load AMD Catalyst™ Proprietary Display Driver - Linux x86 &amp; Linux x86_64."
date: 2012-05-18
forum: General Help
---

### Post by GwibberFooey on 2012-05-18
How do I load this driver onto my computer?  My machine is a Gigabyte A75M-D2H, with and F1 socket and a AMD A6 APU. I propose to download the binary file from [http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run](http://www2.ati.com/drivers/linux/amd-driver-installer-12-4-x86.x86_64.run)  and then save it to SD RAM USB memory stick. Then I will plug in the USB stick and then restart the machine.  Then I will enter the boot menu and set the machine to boot from USB.  Presumably the driver will then load into the firmware.
Is this the correct procedure? I have never done a firmware update before so I don't know anything about it.  Will this cause me to brick my motherboard? I hope not.  Please note that I can't use any linux based features to facilitate this upgrade because I can not boot linux. So I need to load the driver from BIOS.

---

### Post by jim_deadlock on 2012-05-19
I went through hell with my dad's computer trying to get the proprietary AMD driver working so I do sympathise.

I don't know how to install it from a flash drive boot, but what happens when you try to boot normally? Black screen (try kernel module nomodeset)? Are you able to load grub? If you can get a shell (from grub), or root shell even better, then you're almost home and dry and you can do the following.

First you clear out all the fglrx stuff:

```
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
sudo dpkg-reconfigure xserver-xorg

```

... then install your new driver:

```
sudo chmod 755 ./amd-driver-installer-12-4-x86.x86_64.run
sudo ./amd-driver-installer-12-4-x86.x86_64.run
```

**VERY IMPORTANT: if/when it gives you the number options like [1] DO NOT HIT ENTER, you must actually enter the number 1 then enter. I was tearing my hair out for the best part of a day because of this.

Finally, once it's all installed successfully, do this:

```
sudo aticonfig --initial
```

Then reboot normally and you should get your GUI.

---

### Post by GwibberFooey on 2012-05-19
When I try to boot normally, Ubuntu starts to load but then after half a minute or so all out-put to the monitor ceases. So it's not just a black screen, but the monitor actually displays its error message such as "no video" or something similar. 

What should I do to make it go to the GRUB menu ?
If I get to GRUB then what should I do next?

Also, I have a hard disk dock and another computer so I can easily remove the harddisk and look at the file system on it. Can I  mount my harddisk on the other computer then configure nomodeset from there and then return the disk to the original computer ?

---

### Post by jim_deadlock on 2012-05-19
To get the grub screen hold shift during boot, if you can't get to grub then there's something seriously wrong and you might be better off with a fresh install.

Once you're on the grub screen try a) select normal boot but press 'e' to edit the options and add 'nomodeset' (without the quotes), that may get you into the GUI... or b) select recovery mode and you can get a root shell.

nomodeset is usually a temporary thing you do for troubleshooting, there is probably a way to set it permanently but you don't really want to, it's just a way to get you up and running with your new driver.

---

### Post by GwibberFooey on 2012-05-19
I pressed Shift when it starts to boot and it showed "Loading GRUB" on the monitor.  But then after a few seconds the output to the monitor ceases, and the monitor displays its error warning "Entering Sleep Mode". 

I have conducted several attempts at fresh installations, both with Ubuntu 11.10 and Ubuntu 12.04 and this result is identical every time. I have also attempted to install Ubuntu 11.10 onto an other mobo, the Asus F1 A75M and again I got very similar results.

---

### Post by jim_deadlock on 2012-05-19
I think you might want to look in your BIOS settings, that's not right...

---

### Post by GwibberFooey on 2012-05-20
Okay but what should I be looking for in the BIOS settings ?

---

### Post by jim_deadlock on 2012-05-20
Power management settings probably. If not, just go through everything and see if you can spot anything obvious.

---

### Post by GwibberFooey on 2012-05-21
I looked at BIOS but there was nothing there that was the obvious cause of this problem. But I don't understand at least 75 % of the stuff in BIOS therefore maybe the solution is in BIOS and I just don't realize it.

---

### Post by GwibberFooey on 2012-05-22
Progress but still not booting Ubuntu properly.
I am trying to install Ubuntu 12.04 onto a Gigabyte A75M-D2H with an F1 socket and a AMD A8 APU. I am installing from a normal linux iso installation disk, with a normal SATA optical drive.

I went to GRUB and I selected "nomodeset" and then I selected "Install Ubuntu".  The installation seemed to go to completion. I got a GUI and I created a username and password and specified my location and my keyboard layout just like I was prompted to do.  At the end it displayed a message "Installation completed successfully. You must restart your computer to use the new insatllation." So I rebooted and I allowed the machine to (try to) boot from the hard-disk but it was not successful.  

To boot from the harddisk was a failure because a few seconds after it displays "Loading Operating System...", then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

I also tried to install from optical drive without selecting "nomodeset". In that case the installation was a failure because a few seconds after it displays "Loading Operating System..." and "Boot from CD/DVD" then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

I successfully live-booted Ubuntu when I selected "Try Ubuntu without installing" from the GRUB menu with "nomodeset" active. But when I select "Try Ubuntu without installing" from the GRUB menu with "nomodeset" inactive then within a few seconds output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.

Note: I can't get to GRUB without setting the optical drive as first in the boot sequence.  Booting from the harddisk does not work.  In particular, if I visit the boot menu and explicitly select harddisk as the top boot priority then the monitor displays "Loading Operating System..." but nothing more ever happens.  If I don't explicitly visit the boot menu and just allow it to try to boot from the harddisk (which has the highest boot priority by default) then the monitor displays "Loading Operating System..." for a few seconds and then output to the monitor ceases and the monitor displays its error warning "Entering Sleep Mode" or "No Video Input" or something similar.


This problem may not actually be related to the AMD Catalyst™ Proprietary Display Driver - Linux x86 & Linux x86_64.  It might be appropriate if I start a new post at this time.

---

