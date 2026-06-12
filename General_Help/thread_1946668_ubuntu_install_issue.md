---
title: "ubuntu install issue"
date: 2012-03-25
forum: General Help
---

### Post by david99world on 2012-03-25
When I try to install/run ubuntu 11.10 from a liveCD, it just hangs on this screen...

[http://imgur.com/kciVr](http://imgur.com/kciVr)

Any ideas?

I've unplugged all my usb devices other than my death adder mouse and g15 keyboard, tried 32bit and 64bit 11.10 but both do the same thing.

Ran the memory test on the ubuntu install CD and it was fine.

Thanks,

pc specs.. Asus P5Q motherboard Q6700 cpu 4gig dominator 1066mhz corsair 1tb HDD Asus 560ti graphics card

After unplugging all my usb devices (putting a new keyboard in) and disabling firewire on my motherboard in the bios, I get the image below...

[http://imgur.com/MPin2](http://imgur.com/MPin2)

---

### Post by brainwash on 2012-03-25
Hey,

the problem you described looks very similar to this one here

[http://ubuntuforums.org/showthread.php?t=1946307](http://ubuntuforums.org/showthread.php?t=1946307)

So booting with the *nomodeset* kernel parameter should resolve your issue with the nvidia display driver (nouveau).

---

### Post by imachavel on 2012-03-25
a more direct link:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

sounds painful, if the nvidia card isn't onboard, maybe remove it and use onboard graphics while installing? Then when the OS is installed, and you boot to the hdd and load the OS, try sudo apt-get install update in the terminal and sudo apt-get install upgrade as well

then turn off the pc, install your nvidia graphics card in an expansion slot, reboot the pc, and see  if ubuntu recognizes the drivers, you can lspci and post the syntax and return to this thread if you like. OR you could try and visit the web site of nvidia, look for your exact graphics card, and see if there are linux drivers for it, if not try getting windows drivers, then put all that on a flash drive, then put the flash drive in a usb port on the computer you just installed ubuntu on...

BAD idea. because without the proper gpu drivers installed how in the world will you be able to get the OS to load without a blue screen saying no graphics drivers are installed. This is tricky. I'd say the best option is of course to set the no parameter but the OP in that thread even says it's risky because your CPU fan might stop spinning. What a hassle

---

### Post by collisionystm on 2012-03-25
the xorg drivers dont support your card on this release. 

You need to boot with nomodeset

Reboot your computer, keep tapping the up arrow key. you will be at the menu.

Press F6 ( i think ) to choose options. Choose nomodeset and boot.

Once installed you will need to do nomodeset again and then install nvidia drivers.

---

### Post by imachavel on 2012-03-25
ah indeed simple and I made it complicated, as usual. Well that's me, I was looking at all that compiled kernel routine code, and got the idea this guy needed to rewrite a setting config file, which sounds like such a pain, because then he is more of a developer and might have to figure that c code is compiled in binary and the .c file with stdio or whatever is addressing this compiled code, and that that configure file is pointing to settings and simply changing them when he rewrite them. But what a pain one mistake and who knows what would go wrong

f6, like you plan to use a raid set up during install, simply select no mode set from bios, much simpler :lolflag:

---

### Post by collisionystm on 2012-03-25
> **imachavel said:**
> ah indeed simple and I made it complicated, as usual. Well that's me, I was looking at all that compiled kernel routine code, and got the idea this guy needed to rewrite a setting config file, which sounds like such a pain, because then he is more of a developer and might have to figure that c code is compiled in binary and the .c file with stdio or whatever is addressing this compiled code, and that that configure file is pointing to settings and simply changing them when he rewrite them. But what a pain one mistake and who knows what would go wrong

f6, like you plan to use a raid set up during install, simply select no mode set from bios, much simpler :lolflag:


lol. Your genius is to strong for such simple problems! :KS

---

### Post by david99world on 2012-03-25
> **collisionystm said:**
> the xorg drivers dont support your card on this release. 

You need to boot with nomodeset

Reboot your computer, keep tapping the up arrow key. you will be at the menu.

Press F6 ( i think ) to choose options. Choose nomodeset and boot.

Once installed you will need to do nomodeset again and then install nvidia drivers.

excellent, so launch the boot disc, do nomodeset, install the OS (will I still get the option to repartition my HDD, as I currently have windows 7 installed and was hoping to use the partitioner at the start), then restart, install the drivers, then unset "nomodeset"?

Thank you so much all :)

---

### Post by mastablasta on 2012-03-25
> **david99world said:**
> excellent, so launch the boot disc, do nomodeset, install the OS (will I still get the option to repartition my HDD, as I currently have windows 7 installed and was hoping to use the partitioner at the start), then restart, install the drivers, then unset "nomodeset"?

Thank you so much all :)

no, after installation then restart with nomodeset again and then install the drivers.

also suggets you use windows disk manager to repartition the drive. and make sure you defragment the disk first a couple of times (2) before doing that and run a checkdisk after that otherwise it could get ugly.

---

### Post by david99world on 2012-03-25
You know with regards to "nomodeset" will it just load in a very simple GUI resolution like 800x600 or will it be all command line based?  Just I don't feel confident being able to download the nvidia drivers etc via command prompt.

Thank you very much for your advice.

---

### Post by collisionystm on 2012-03-25
> **david99world said:**
> You know with regards to "nomodeset" will it just load in a very simple GUI resolution like 800x600 or will it be all command line based?  Just I don't feel confident being able to download the nvidia drivers etc via command prompt.

Thank you very much for your advice.


It SHOULD load a gui for you.

If you do happen to reach a command line

sudo bash

apt-get remove xserver-xorg-video-nvidia  ( think )

lightdm restart

---

