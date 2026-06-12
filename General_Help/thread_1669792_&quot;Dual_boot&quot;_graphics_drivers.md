---
title: "&quot;Dual boot&quot; graphics drivers"
date: 2011-01-18
forum: General Help
---

### Post by Taijitu on 2011-01-18
Hello, sweet and dear ubuntuforums :-).

I have tried to search the web and the forums for this, but I can only come up with very generic keywords, leading me to manually browse through thousands of threads to find something on this, so I will try to make a new one.

What I would like to do is have a dual boot option of the same ubuntu system, only using different graphics drivers.

For everyday work, browsing etc. the nouveau drivers are rather superior to the proprietary, imho, and also give me better dimming options on my laptop and often better battery life.

However, I sometimes play some wine games, requiring the proprietary drivers...

So could it be possible to have a better way to switch between these drivers, perhaps with separate entries in grub or so? 

In advance, thank you for any advice.

---

### Post by Hippytaff on 2011-01-18
a possible solution might be to install a dual boot ubuntu system with a shared /home partition, so that you can access your files and settings from both, but have different graphics drivers for each. However I've never tried this.

---

### Post by Taijitu on 2011-01-18
I have considered that, but then the installed software would not be in sync which is kind of a nuisance...

---

### Post by Hippytaff on 2011-01-18
What do you mean by syncing the software? can you give me an example?

---

### Post by Sylos on 2011-01-18
> **Hippytaff said:**
> a possible solution might be to install a dual boot ubuntu system with a shared /home partition, so that you can access your files and settings from both, but have different graphics drivers for each. However I've never tried this.

+1 - Thats what I would do.

I have actually done a similar thing for Ubuntu and Ubuntu Studio and KXStudio. I have a shared partition that both ubuntu studio and Kxstudio use as /home. I then also have a storage partition on another drive that is mounted at boot by both Ubuntu Studio and Ubuntu.

Im not sure if there are any alternative ways of doing this easily. I suppose it may be possible to use a boot parameter that tells xorg to use a particular xorg.conf that points to a specific driver. If it is possible its above my head.

---

### Post by Taijitu on 2011-01-18
@Hippytaff
The installed software in ubuntu is in the root partition. Dual booting as you suggest would mean that installed software in the one system would not be in the other, so I would have to install everything twice..

---

### Post by Taijitu on 2011-01-18
Ack... Double post, sorry >.<

---

### Post by Sylos on 2011-01-18
Reading the Grub 2 guide here

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

...it does seem to be possible to create a custom boot entry using the basic guidance they provide. Essentially it appears you can copy a working boot entry and then fiddle with it until you get what you want.

Still not sure what and where you would alter the grub files to get it to choose a different xorg.conf though...

Im at work at the momnet but I'll look around again later and post bakc if I hit anything useful looking.

---

### Post by Hippytaff on 2011-01-18
> **Taijitu said:**
> @Hippytaff
The installed software in ubuntu is in the root partition. Dual booting as you suggest would mean that installed software in the one system would not be in the other, so I would have to install everything twice..
 
Right - I see what you mean, and getting both installations to point at the one root partitions could get messy (and fudge the whole fix in the first place) hmmm

---

### Post by Taijitu on 2011-01-18
@Sylos

It sound possible... Not bad.

Thanks a lot for your time! :-D

---

### Post by mc4man on 2011-01-18
Depending on your system and the method chosen it should only take about 1 min or less to switch from nvidia to nouveau to nvidia, ect.

Jockey (hardware drivers) will do everything for you though is a hair slower than doing manually thru update-alternatives + 3 commands

A possible downside to jockey is it removes your xorg.conf while manually you mv it to a .bak
(doesn't matter if you haven't made custom entries in xorg.conf

So jockey is a bit better because you can't mess the switch up though slower because you remove or re-install the drivers (the drivers are accessed thru the apt cache so they aren't actually downloaded again

Manually is quicker because nvidia is left installed, you just switch the default and run 3 commands

---

### Post by Sylos on 2011-01-18
> **mc4man said:**
> Depending on your system and the method chosen it should only take about 1 min or less to switch from nvidia to nouveau to nvidia, ect.

Jockey (hardware drivers) will do everything for you though is a hair slower than doing manually thru update-alternatives + 3 commands

A possible downside to jockey is it removes your xorg.conf while manually you mv it to a .bak
(doesn't matter if you haven't made custom entries in xorg.conf

So jockey is a bit better because you can't mess the switch up though slower because you remove or re-install the drivers (the drivers are accessed thru the apt cache so they aren't actually downloaded again

Manually is quicker because nvidia is left installed, you just switch the default and run 3 commands

This is probabbly a better solution than mine - at least a lot easier. I have been trying to figure out how to get two xorg.conf files to be usable and I cant figure it out. If the files where named differently they would not be recognised by X11. The only way it would work is if the boot entry started a script that replaced the xorg.conf with one from a different location.

You would probably be better writing a shell script that stops gdm, replaces the xorg.conf with another one and then restarts X. You would need one to go either way (for each purpose).

I have never used Jockey but it seems like the thinking mans solution.

---

### Post by alazou on 2011-06-03
I know this is kind of old but I remember writing a script in fedora that would switch from nouveau to nvidia. I would like to do the same in ubuntu but I can't seam to get it right. If someone can help that would be appreciated. What I'm trying to do thus far when I switch to nouveau :

1- ```
update-alternatives --config gl_conf 
```
to select /usr/lib/mesa/ld.so.conf when I want to use nouveau or
the other alternative for nvidia. How do I auto select using this command without the need for user input ?

2- ```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

```
3- add ```
nouveau.modeset=1
``` to kernel command line, using sed. what would be the best way to do that ? I'm kind of unfamiliar with grub 2

4- I need to prevent nvidia from loading. I noticed that it is not enough to add blacklist nvidia to /etc/modprobe.d/blacklist.conf. Do I need to configure dkms in some way to prevent it from loading nvidia ? How would I do that.

I'm willing to make my script available if I manage to make it work ;)

---

### Post by oldfred on 2011-06-03
I have not tried it, but saved these links:

Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)
nVidia may blacklist nouveau:
/etc/modprobe.d/nvidia-installer-disable-nouveau.conf
or
/etc/modprobe.d/nvidia-graphics-drivers.conf

---

### Post by alazou on 2011-06-03
I read your links but I don't think it will help, or rather I don't like their solutions.
I want to avoid having to use nvidia-xconfig generated xorg.conf because it completely ignore the last 2-3 years of xserver development.

I almost got it though. But something is missing. I can't get the kernel to call nouveau modesetting, and the 3D acceleration of nouveau doesn't work with kwin if I don't completely uninstall nvidia. 

What would be helpful would be a way to know exactly what happen when we uninstall the blob. Would this information be in the deb files of nvidia-current ?

---

