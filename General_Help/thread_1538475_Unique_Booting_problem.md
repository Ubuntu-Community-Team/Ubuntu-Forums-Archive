---
title: "Unique Booting problem"
date: 2010-07-25
forum: General Help
---

### Post by lukster91 on 2010-07-25
Hello all,

I've just built a new computer. I've got 2 HDD's, One is 500GB hosting Windows 7, working perfectly. The other is a 320GB hosting Linux Ubuntu 10.04. With a little bit of hassle, I've managed to get Ubuntu installed. 

Whilst I was using the LiveCD, sometimes it just wouldn't boot into Ubuntu. Displaying a rapidly flashing "_" just after the selection of whether I wanted to go into 'Installing', or 'trying Ubuntu our with any change to my computer'.

After several reboots, and selecting the installation option, it worked. (I had to unplug my windows HDD in order for the volume selector in the installation to see it.)

Once getting Ubuntu installed, I've managed to boot into it once since (with some hassle). But I can't seem to load it any more. After the GRUB selector, I get this same flashing "_". 

I don't believe this to be a HDD problem as I believe the GRUB is installed to the 320GB HDD, and boots into that every time.

I think this may be a BIOS problem. Though I'm just guessing and wouldn't know the first thing about how to update it, or change the settings so it works. The motherboard is a new ASUS P7h55-m.

I don't believe this to be a graphics card problem, as this Hard drive, graphics card and Ubuntu have all worked in a previous computer without hassle. Though, just incase you think it is, the Graphics card I have is an nVidia GeForce 6800 LE. 

Any ideas?

Thanks.

Luke Bellamy

---

### Post by lukster91 on 2010-07-25
Anyone got any idea?

---

### Post by oldfred on 2010-07-25
If you uninstalled the windows drive then the install only saw Ubuntu so it will not show a menu unless you hold down the shift key from BIOS boot until it shows. So it may be a video issue or not.

Try getting the menu. I have a newer nvidia card and had to manually add on first boot nomodeset in place of quiet splash on the kernel line. Use e at the menu if you can get to it and edit the line.

If not post this, but if grub is ok it may not help:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by theOGRE on 2010-07-25
I don't know if this would help you or not. I'm having a problem with usplash (see [here]("http://ubuntuforums.org/showthread.php?t=1513557")). I get a flashing underscore on a black screen at boot time. You can try altering your 
'/boot/grub/menu.lst'   file. May have to use a live cd to get to it if you can't boot. Then change your kernel's section to not say 'splash' or 'quiet'. That makes me not get the underscore of doom. Like I said, I don't know if it'll help as we obviously have different problems.

---

### Post by lukster91 on 2010-07-25
> **theOGRE said:**
> I don't know if this would help you or not. I'm having a problem with usplash (see [here]("http://ubuntuforums.org/showthread.php?t=1513557")). I get a flashing underscore on a black screen at boot time. You can try altering your 
'/boot/grub/menu.lst'   file. May have to use a live cd to get to it if you can't boot. Then change your kernel's section to not say 'splash' or 'quiet'. That makes me not get the underscore of doom. Like I said, I don't know if it'll help as we obviously have different problems.

Problem is I can't boot a LiveCD either. I just can't get Ubuntu to work on this computer.

I've worked out that if I unplug the HDD I want to install Ubuntu too, it boots into LiveCD absolutely fine. But then its not plugged in, for me to install it.

---

### Post by oldfred on 2010-07-25
Have you tried f6 on the initial cd load. You can add nomodeset or other parameters to get it to boot.

Have you reviewed BIOS settings. It may be something in SATA or PATA drive set up in BIOS

---

### Post by lukster91 on 2010-07-26
I have reviewed BIOS and I have checked everything I think would have affected it. 

Can you explain this nomodeset thing more? I don't quite understand what you mean. 

Thanks!

---

### Post by oldfred on 2010-07-26
this is all the info I have on video. nomodeset works for many video cards but some need other settings.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

(from Fedora)
All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 
nouveau.modeset=1

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by lukster91 on 2010-07-29
Thanks for all your help, but I believe the problem is unique to my computer, and there is no solution short of replacing my second hard drive.

I mentioned the Hard drive problems earlier. Changes to method of installation (be it with the graphics card or other)... I tried everything suggested on this forum, with no affect.
I also tried using the wubi installer. I installed it to my 2nd hard drive, with similar problems to installing it from the LiveCD. Couldn't get it to work.

I then removed that and installed it on my main hard drive so it wasn't interacting with the other perhaps "faulty" Hard drive. Works fine.

It's not the installation type I want. But at least I know have my beloved Ubuntu on my Desktop alongside windows in some form... Until I buy a new hard drive and try again. 

I will leave this thread as unsolved, as I don't believe there is a solution. However, you are free to prove me wrong, I will try anything anyone suggests.

---

