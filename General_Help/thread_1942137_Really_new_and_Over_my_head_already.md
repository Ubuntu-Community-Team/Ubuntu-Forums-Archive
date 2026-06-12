---
title: "Really new and Over my head already"
date: 2012-03-16
forum: General Help
---

### Post by blackflame0729 on 2012-03-16
Yeah, like the title says, I'm really new and trying to find out but I have like 7 tabs open and none of them seem to work.

I am trying to install Ubuntu on my laptop via Wubi and my laptop will turn off the backlight when it boots into Ubuntu (I can hold a flashlight up to the screen and just make out the login of Ubuntu).  I am reading 2 major fix threads.  ([http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535) and [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)).

I have already changed \ubuntu\install\wubildr-disk.cfg to include nomodeset but that doesn't work.  Then, I tried going to the grub menu and all I got is "Ubuntu with Linux - generic" and "Ubuntu with Linux - generic(recovery mode)"  Both modes of which result in just a black screen.  I am trying to change my acpi and they say to go into the terminal but I cannot seem to reach it.  I tried going into the command line and then "terminal_input" but "gksudo gedit /etc/default/grub" wont read after that.  I was wondering if there is any ways to change the acpi maybe in windows editing a cfg file or by using/edit commands before booting.

My wubildr-dsk.cfg:
> loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
search --set=diskroot -f -n /ubuntu/disks/root.disk
probe --set=diskuuid -u $diskroot
linux /vmlinuz root=UUID=$diskuuid loop=/ubuntu/disks/root.disk preseed/file=/ubuntu/install/preseed.cfg wubi-diskimage ro quiet splash nomodeset acpi=off
initrd /initrd.img
boot

---

### Post by bcbc on 2012-03-17
The wubildr-disk.cfg is only used for the very first boot. Now that you see the grub menu, you have to edit it directly at boot. (Press 'E' on the menuentry, edit, and then Ctrl+X to boot)

I don't think the acpi=off will help the backlight. It might, but please post your computer brand/model/graphics card (intel?) and then it'll make it easier to search on it.

Thanks

---

### Post by blackflame0729 on 2012-03-17
Well its working now.

What I did was uninstalled and edited the wubildr-dsk.cfg to start with 'nomodeset' and then reinstalled and that worked, then I forgot to change in inside the OS so I ended up taking a flashlight to the screen so I can see and going through the terminal there to edit the grub to do 'nomodeset'.

---

### Post by winh8r on 2012-03-17
Well done!

Glad you got it going, I am particularly impressed by the "flashlight" method, much more resourceful than just saying "the screen went black and I couldn't do anything." =D>\\:D/=D>

---

### Post by blackflame0729 on 2012-03-17
> **winh8r said:**
> Well done!

Glad you got it going, I am particularly impressed by the "flashlight" method, much more resourceful than just saying "the screen went black and I couldn't do anything." =D>\\:D/=D>

Lol thank you.  Using a flashlight is the easiest way to find out if the backlight on a laptop has gone out and I figured that I would just read up on changing boot options within the already installed OS and did it that way.  Goto get the job done somehow.  I didn't want to reinstall again with the one time fix of changing the install file because I was playing around last night and installing apps and such so that would have been a pain.

---

### Post by grahammechanical on 2012-03-17
Over your head? No way! Up to your neck, may be.

Regards.

---

