---
title: "Please help I am desperate"
date: 2010-02-11
forum: General Help
---

### Post by stevecrowther on 2010-02-11
This is a cry for help.

I have installed Ubuntu and tried to activate the enhanced effects. Ubuntu then updated my Nvidia driver and asked me to activate it. 
Now all I get after Grub is a black screen. I can enter my password but I can't see anything.
How do I get Linux back running again after my catastrophic driver update if I can't see the screen.
All help would be greatly appreciated....as you can probably guess I am a very frustrated newbie.

Thanks,

Steve

---

### Post by miniyak on 2010-02-11
I know this is your first post so its ok... but you probably have better luck w/ a title like "not booting after installing nvidia driver"

First thing you may want to try is booting into safe mode, From the grub menu you should be able to select this option

What version of Ubuntu are you running? Whats your hardware? (another important thing to mention, for future referenced)

This has happened to me before... I know how it feels.

---

### Post by akakingess on 2010-02-11
> **miniyak said:**
> I know this is your first post so its ok... but you probably have better luck w/ a title like "not booting after installing nvidia driver"

First thing you may want to try is booting into safe mode, From the grub menu you should be able to select this option

What version of Ubuntu are you running? Whats your hardware? (another important thing to mention, for future referenced)

This has happened to me before... I know how it feels.

+1 on this idea, but you could also just try booting from a previous kernel and see if that will allow you to at least get to the desktop. Otherwise, miniyak is correct in that safe mode is a good way to at least start the troubleshooting process.

---

### Post by stevecrowther on 2010-02-11
Thanks for the advice.

I am running 9.10 and just see a black screen before the login screen. I have found out how to log in to safe mode and get a root prompt, but I don't know what commands to enter.

Any help greatly appreciated.

Steve

---

### Post by dillinger417 on 2010-02-11
helpful commands:

uname -a -- will give you a nice description of your system, stuff like kernel version number, variant of ubuntu install ( x64, etc)

dmesg or tail -- will give you system messages, u can look for errors

shutdown -r now -- will restart your computer

lspci |grep -i vga -- will list your pci hardware and likely find your video card (try just lspci if u don't see it )

lsmod |grep nvidia -- will likely find your nvidia driver/module if it loaded w/o problems

** One option might be to use envy to try to re-install your driver. envy is a nice tool to use to update your ati or nvidia driver (afaik still an active tool). If you don't have it you can install it via "sudo apt-get install envyng-core" and run it by the command "envyng -t" ( -t for text-based )

Hope that helps.

---

### Post by Richard1979 on 2010-02-11
Try running:

mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak 
# (this will create a backup)
nvidia-xconfig 

More help:
[http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html](http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I know they are specific to earlier versions but they should still be relevant.

This may help if you really can't get in after all that:

```
sudo apt-get remove compiz
 sudo apt-get remove compiz-core
  sudo reboot

```

---

### Post by samantha_ on 2010-02-11
first, lets get rid of the black screen.
from 9.04 (or is it 9.10?) onwards, there is no need for xorg.conf.
so...
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo shutdown 0 -r
```

second. whats your graphics card?

---

### Post by lidex on 2010-02-11
> **stevecrowther said:**
> Thanks for the advice.

I am running 9.10 and just see a black screen before the login screen. I have found out how to log in to safe mode and get a root prompt, but I don't know what commands to enter.
Steve

```
startx
```

---

### Post by bronquel on 2010-02-12
after i switched from windows, where i needed to reinstall windows every couple of months to fix issues, I kinda got in the habit with linux.  I'll break something, and copy all my data off (sometimes using a live cd cause i've set the graphic to 320x240, other times i've wrecked this or that), and reinstall.  

There definitely is a more elegant solution than reinstalling, but from what it sounds like the visual effects were working, and you can gage the amount of time to back up and reinstall.  Depends on your time frame and patience level.  Ubuntu tweak helped me (after i had my graphics drivers installed) to get the fancy stuff.  hope that helps.

---

