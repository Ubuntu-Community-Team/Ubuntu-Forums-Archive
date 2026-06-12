---
title: "Activated nvidia drivers now can't see login screen"
date: 2009-12-15
forum: General Help
---

### Post by cje123 on 2009-12-15
Hi all,
I am new to Ubuntu and these forums. I have tried searching for this problem, and am aware of a few that have had it, though I am completely lost when it comes to fixing it.

My system specs:
Intel P4 3.2ghz
1gb ram (2x 512mb)
2x WD 160GB IDE drives (XP on Master, Ubuntu on Slave)
Nvidia 7600GT

I installed Ubuntu from windows xp using the LiveCD "Install from windows" it installed it fine, rebooted, I booted into Ubuntu via GRUB, and it started configuring itself. However, it kept failing to install due to an Ernor 5 Input/ Output error. I google that, and found that it might be ram, I removed 1 stick and it installed perfectly.

I was starting to use Ubuntu nicely for a few minutes when it said that nvidia drivers could be activated. I chose to activate 185 (reccomended). It downloaded, installed so I rebooted but after the small white logo I don't get a login screen now.


THE PROBLEM:
I get a black screen with Unbuntu 9.10 white text flashing quite rapidly. (Where it should be going to the login screen) I have tried Ctrl + Alt +F2 but it doesn't work. I have tried booting into recovery mode but am totally lost.


If someone could guide me I would appreciate it enormously. Please bear in mind that I know nearly nothing of Linux so far, so it'll have to be spelled out, or point me in the right direction at least. My first foray from windows and I'm stuck. Good start eh?:(

---

### Post by cje123 on 2009-12-16
Anyone? Please.

---

### Post by Zoot7 on 2009-12-16
Give this a shot, whenever it boots up hit Ctrl + Alt + F1, logon with your username and password and enter this:
```
sudo rm /etc/X11/xorg.conf
```
Then reboot, that'll get you up and running with the normal Vesa drivers. De-activate the driver to uninstall it using the Hardware Drivers tool.

TBH activating the drivers from the Hardware Drivers tool has never worked for me.

Then, Download the latest driver from here, and stick it in your home directory (/home/your_username):
[http://uk.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run](http://uk.download.nvidia.com/XFree86/Linux-x86/190.42/NVIDIA-Linux-x86-190.42-pkg1.run)
That'll give you a script to run to install the driver.

Then do this to install it:
```
sudo service gdm stop
```
That'll take you to a black screen with just the command prompt.
Then do this to install the driver:
```
sudo sh NVIDIA-Linux*
```
Accept all the prompts including the one to generate xorg.conf, then either reboot, or enter
```
sudo service gdm start
```
see if that works. 
That'll install the driver manually from Nvidia rather than the Ubuntu repositories, I've always found this to be a better option.

If you'd rather install it easier you could give the automated installer Envy a shot:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by cje123 on 2009-12-16
Hi, thanks for replying. I can't even do that. The screen flickers like crazy, alternating between black and some White writing with Ubuntu 9.10 etc. I tried what you said, but the keyboard seems
only to respond in the split second moments when I can see the prompt.

Is there a way to do this in recovery mode? Or is it just easier
to reinstall? I installed it from windows, and I know my gfx works alright in that.

---

### Post by Zoot7 on 2009-12-16
> **cje123 said:**
> Hi, thanks for replying. I can't even do that. The screen flickers like crazy, alternating between black and some White writing with Ubuntu 9.10 etc. I tried what you said, but the keyboard seems
only to respond in the split second moments when I can see the prompt.

Is there a way to do this in recovery mode? Or is it just easier
to reinstall? I installed it from windows, and I know my gfx works alright in that.
No, there's no need to re-install. ;) There's nothing wrong with your card either, it's just that kernel updates in Ubuntu (or linux in general) have a habit of flushing graphics drives down the toilet sometimes.

I got that exact same problem with the nvidia card in my laptop about 2 or so weeks ago. I removed xorg.conf from recovery mode and just installed the driver the way I posted above and that sorted everything.

Or what you could do, if it's easier for you, you could just boot off a live CD and delete xorg.conf from your Ubuntu partition that way.

---

### Post by cje123 on 2009-12-16
Ok, booted via livecd.

Where is the xorg.conf located, and if I delete it do I have to do anything then? Or will it reconfigure itself with defaults on reboot on hdd?

Also, I'm getting loads of input/output error messages with 2 wicks of RAM installed. I memtested both individually and in dual channel wihout probs. However if I remove one these messages go. Is this something I should worry about? I can boot off livecd just fine, but for installation I had to
remove 1 stick on first boot.

EDIT- the ubuntu folder on my hard dive doesn't have anything it? I've booted via livecd, opened up the 2nd hdd where ubuntu is installed, there is an ubuntu folder there but it reports it as empty??

---

### Post by Zoot7 on 2009-12-16
> **cje123 said:**
> Ok, booted via livecd.

Where is the xorg.conf located, and if I delete it do I have to do anything then? Or will it reconfigure itself with defaults on reboot on hdd?

Also, I'm getting loads of input/output error messages with 2 wicks of RAM installed. I memtested both individually and in dual channel wihout probs. However if I remove one these messages go. Is this something I should worry about? I can boot off livecd just fine, but for installation I had to
remove 1 stick on first boot.

EDIT- the ubuntu folder on my hard dive doesn't have anything it? I've booted via livecd, opened up the 2nd hdd where ubuntu is installed, there is an ubuntu folder there but it reports it as empty??
You should see your Ubuntu partition along with all other hard drives connected under the Places menu.
Select your Ubuntu partition, it'll probably have a name like X amount GB Media etc. , navigate to the etc directory, then X11 and you'll see xorg.conf. That's the file to delete and reboot.

Not sure about the I/O errors, tbh I haven't found the live CD of Karmic to be the most trustworthy, I got manys a report of a failing hard drive with it. If memtest says you're in the clear you're fine i'd say. :)

---

### Post by cje123 on 2009-12-16
Well it seems that I've messed something up as i booted into windows, and the ubuntu folder is corrupted. Can't access anything. I tried booting ubuntu from the hard drive and I just go to the GRUB and seems it couldn't find anything. I booted back into xp, looked at the hdd and right clicked and went to properties. There's only 50mb worth of files on there?! Seems the install has corrupted or something?

I tried uninstalling ubuntunfrom xp add/ remove programs and it reports it as corrupted! 

Not sure how to sort this now, as The GRUB bootlader is still installed and gives me option to boot into ubuntu when switching the pc on, but there ain't anything there to load.

I could reformat the D drive where I've got the corrupted Ubuntu, but am afraid of what will happen to the boot menu.

Thanks for your help so far,

---

### Post by Zoot7 on 2009-12-16
You've installed with Wubi (installed with the liveCD from Windows) it seems. TBH I've never used it so I've no idea how to fix your problem. Normally XP wouldn't be able to see the Ubuntu partition at all on account of not being able to read the filesystem.
Don't worry about the bootloader, Wubi doesn't install grub to your hard drive, it just adds an entry to the Windows bootloader that lets you boot into the image it places on your hard drive. You can edit (I'm assuming) XP's boot.ini to get rid of said option.

TBH were I you, I'd install it to the hard drive rather than with Wubi, it'll perform a lot better.
In other words, boot off the liveCD, partition your hard drive and install Ubuntu on it. The installer is quite easy to use, it'll even handle the partitioning of the hard drive for you and set up Grub to boot both Windows and Ubuntu accordingly.

---

### Post by 11g on 2010-01-08
grub has a recovery mode: you can get a shell and access the files from terminal
in the shell you can change the xorg.conf by editing it with nano for example

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241)

run the command: lspci | grep -i vga 
It lists the device id of your card. Mine is:
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

to edit the xorg.conf type and press enter: nano /etc/X11/xorg.conf
edit the device section: add busid with the previously listed number:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Busid    "PCI:2:0:0"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

To save changes in nano press ctrl+x, y, press enter
reboot with init 6

---

If you decide to reinstall ubuntu you can do this after activation of the nvidia driver but before reboot
in this case type sudo before each command

---

### Post by ScrewBaxster on 2010-09-24
This worked for me. Booted up LiveCD, opened a terminal, opened nautilus with root and deleted xorg.conf. Rebooted PC and it worked perfectly fine, Thanks.

---

