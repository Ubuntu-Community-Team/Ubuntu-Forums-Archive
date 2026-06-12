---
title: "Unable to boot after changing resolution using startup-manager"
date: 2010-05-31
forum: General Help
---

### Post by Taiyou on 2010-05-31
Hello,

I am rather new to ubuntu so it's possible that I've done something very wrong, or maybe it's easy to fix (which I hope).

I am running ubuntu 10.04 on my packard bell laptop (TJ65) with an nvidia geforce G105M. While booting, the grub menu and splash logo have a very small resolution, so I wanted to make it a bit larger.
I used startup-manager to adjust the resolution. After a reboot I noticed that the grub menu had a better resolution but it didn't go over to the splash but to the recovery menu...
I tried the resume option, but I end up back at the recovery menu. So I tried the failsafe mode, booting in low-graphics.

I get this error message:

Ubuntu is running in low-graphics mode

The following error was encountered. You may need to update your configuration to solve this.

(EE)[drm]failed to open device
(EE)Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I keep returning at this error message and don't really have a clue about what to do. Does anybody have some suggestions?

---

### Post by WinRiddance on 2010-05-31
Can't you boot into low graphics mode and then access the startup manager from there, in order to change the resolution back to 800 X 600 or whatever it was before? I'm not even sure if I understand your post correctly because the startup manager, as far as  know, only changes the resolution during the boot process.
To change your resolution permanently to something that you like you'd have to get into the START menu then SYSTEM then PREFERENCES followed by clicking on the MONITORS symbol. If you have an updated graphic chip with manufacturer supplied drivers you may also change the resolutions within some type of "control panel" for your particular graphic chip. I've never heard of changing the resolution with the startup manager though ....

Perhaps it might help to power off completely, followed by powering back on a minute or two later, and then letting the system do whatever it wants for a few more minutes **uninterrupted**. Just ignore it and see what happens? Sometimes it's just a matter of being a little bit more patient. I never change the startup options since the system boots into Ubuntu by default anyway so I don't care what the resolution is at that point. Once I'm logged in everything appears as I want it to appear and only then is the appearance/resolution really important ... at least to me that is. Good luck!

---

### Post by Taiyou on 2010-05-31
The resolution after the boot is... was fine. It is because I dual boot with windows that I was thinking about adjusting the resolution. Didn't think it would do much harm.
I tried booting into low graphics mode to access the startup manager, but problem is that I'm not able to even boot in low graphics mode. 
I took [a picture of where it stops doing anything]("http://i183.photobucket.com/albums/x135/nickman_/P310510_2001.jpg"). I've tried just leaving the computer, in hope that after a while something would happen, but nothing :-/

I also tried the other options in the menu, creating a new configuration or using a back-up configuration. But those just do nothing and instantly bring me back to the menu.

---

### Post by oldfred on 2010-05-31
Startup manager only edits the grub files. Your error message is after grub and into booting and it is xorg.conf.d which is your video config file. Did you install/uninstall nvidia?

I would try this and see if it boots.
 press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

You could see if you have a back up of your xorg or edit the xorg also. Not sure what settings that would be.

---

### Post by Taiyou on 2010-05-31
> **oldfred said:**
> Startup manager only edits the grub files. Your error message is after grub and into booting and it is xorg.conf.d which is your video config file. Did you install/uninstall nvidia?

I would try this and see if it boots.
 press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

You could see if you have a back up of your xorg or edit the xorg also. Not sure what settings that would be.
I tried pressing e and editing the lines. I'm still stuck at recovery menu. I didn't touch the nvidia installation. But it might be best to reinstall. But is it possible not being able to boot correctly?

After trying to boot with the adjusted lines, the error message changed into:

(EE)[drm]failed to open device
(EE)VESA: Kernel modesetting driver in use, refusing to load
(EE)FVDEV(0):EGA/VGA planes are not yet supported by the fbdev driver 

Isn't there a way I could reset the xorg file? So I can boot using the standard driver instead of the nvidia driver? Or isn't that the problem?
Thanks for the help.

---

### Post by oldfred on 2010-05-31
I do not know what settings are required.

It says it is using the failsave version.

/etc/X11/xorg.conf.failsave

Do you have an xorg.conf in /etc/X11?

Some more info:
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by Taiyou on 2010-05-31
I seriously have no clue what's wrong. 
I tried the "echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf"

but that didn't work, and it seemed I didn't have a xorg.conf file. So I added one. First I tried a backed up version of the nvidia one, but that one didn't work, then I tried one from the links you gave you, using vesa driver. Still no boot :-S

I don't get a DRM error anymore, but I still get "(EE)Failed to initialize GLX extension (Compatible NVIDIA X driver not found)"

---

### Post by oldfred on 2010-05-31
Can you boot to a terminal, either recovery or editing of boot lines?

I would then try installing:

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

---

### Post by Taiyou on 2010-05-31
> **oldfred said:**
> Can you boot to a terminal, either recovery or editing of boot lines?

I would then try installing:

sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot
"sudo apt-get install nvidia-current nvidia-settings" told me that I already have the most recent version
"sudo nvidia-xconfig" this created a new xorg.conf file because the previous one seemed to be gone again
after the reboot only notable diffrence was that I could see the nvidia logo for about 1/2 second :-/
then it was back to the recovery menu... :(

---

### Post by oldfred on 2010-05-31
I am out of ideas. 

Possibly check error logs. 
/var/log/

Or add someother config settings to boot line like noapci etc. There is  a long list of parameters but most are for old systems with hardware issues. You should check on your system to see if others had to use special settings.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by Taiyou on 2010-05-31
Thanks for all the help!
I'll check that out when I have some spare time.
If there's any progress I'll post it here :-)

---

