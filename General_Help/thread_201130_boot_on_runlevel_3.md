---
title: "boot on runlevel 3"
date: 2006-06-21
forum: General Help
---

### Post by odysseus.lost on 2006-06-21
Hi,

I tried booting in runlevel 3 by editing the boot on grup by deleting the splash screen and adding either a 3 or an init 3 in the end. But it still boots up in runlevel 5.

Any clues?

Cheers!

---

### Post by odysseus.lost on 2006-06-21
OK, this is really annoying... I found on the following post
[http://www.ubuntuforums.org/showthread.php?t=200228&highlight=runlevel](http://www.ubuntuforums.org/showthread.php?t=200228&highlight=runlevel)
that Ubuntu has only 2 runleves... (OK it has 0,6,s,S I presume
runlevel 1: single user mode
runlevel 2: multi user mode with X

Usually runlevel 2 of Ubuntu us runlevel 5 while RL2 is not used and RL3 is multi-user mode withtout GUI.... what i am looking for.... so how is it possible to start Ubuntu into console mode??

---

### Post by thasheep on 2006-06-21
On ubuntu, runlevel 2 is default. This can be changed by modifying the line 'id:2:initdefault:' in /etc/inittab
However, this in itself won't do much, unless you change it to 1 (single user). As you might know, setting it to 0 (shutdown) or 6 (reboot) is stupid. By default 2-5 are all multi-user with gdm (X11). This can be changed. Eg to prevent X loading automatically on runlevel 4
```
sudo rm /etc/rc4.d/S??gdm
```If you're running kubuntu, it's probably kdm rather than gdm. The files in /etc/rc[runlevel].d/ are all symlinks to services (in /etc/init.d) to start when starting the runlevel have a look at 'ls -l /etc/rc?.d'. You can recreate the symlink by copying it from another runlevel or by doing ```
cd /etc/rc[runlevel].d
sudo ln -s ../init.d/[service_name] S[start_order][service_name]
```

---

### Post by odysseus.lost on 2006-06-22
Thanks for that.... although I am still wondering that since runlevels are going in sequence and since gdm is loaded on runlevel2 what is the point of removing from any of the subsequent runlevels. Anyway, I ll have a look and see what's going to happen...

---

### Post by gwpritch on 2006-06-22
I think there is a misconception about the runlevels. The system starts all services defined in /etc.rcS.d then enters which ever runlevel is defined in /etc/inittab...rc2.d by default and starts the services defined there. It does not run any other runlevels until shut down or rebooted..0 & 6.
If you are booting into runlevel 2 you can boot into the console by removing the simlink to gdm in /etc/rc2.d  SXXgdm (where x is the number defining the sequence of service startup
The files contained in the runlevel directories are merely simlinks to the scripts contained in /etc/init.d

---

### Post by odysseus.lost on 2006-06-22
[QUOTE=gwpritch]I think there is a misconception about the runlevels. The system starts all services defined in /etc.rcS.d then enters which ever runlevel is defined in /etc/inittab...rc2.d by default and starts the services defined there. It does not run any other runlevels until shut down or rebooted..0 & 6.
If you are booting into runlevel 2 you can boot into the console by removing the simlink to gdm in /etc/rc2.d  SXXgdm (where x is the number defining the sequence of service startup
The files contained in the runlevel directories are merely simlinks to the scripts contained in /etc/init.d[/QUOTE]
Cheers... but I would still like to have the option of booting into multi-user graphical mode determined on the boot loader.... Btw, do you imply that after runlevel S, the sytem goes directly to runlevel 2 bypassing runlevel 1???

---

### Post by gwpritch on 2006-06-22
level 1 or single user mode is a level usually reserved for system administration.
I am not sure how you would change via the boot loader, however you can change run levels using the telinit command...ie if you are in runlevel 3 you can change to runlevel 2 by issuing 

```
telinit 2
```

To change back and forth from console to X edit the 'console' gdm simlink.
eg rename S99gdm to K99gdm. I believe this kills the service. Then use telinit to switch back and forth.

---

### Post by thasheep on 2006-06-22
The runlevel can be specified in the grub entry. Simply add the number at the end of all other boot options.
If you would like to automatically have two entries (for different runlevels) for each kernel and can do without the "rescue" mode, you could alter the automagic section of /boot/grub/menu.lst to that effect. Eg, replace that section with (the lines starting with # are used the ones with ## are skipped)....```
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=ro quiet splash vga=791

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=2

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(rl3) 3

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false
```
Obviously sub in the drive and partition numbers from before.

---

### Post by odysseus.lost on 2006-06-23
[QUOTE=thasheep]The runlevel can be specified in the grub entry. Simply add the number at the end of all other boot options.[/QUOTE]

I know that but it simply does not work because ubuntu has two runlevels. You can try in your machine two.... the only number actually working are 0, 1, 2, 6. What I think I have to do is hack a bit the inittab file and also the corresponding rc#.d directories.

[QUOTE=thasheep]
If you would like to automatically have two entries (for different runlevels) for each kernel and can do without the "rescue" mode, you could alter the automagic section of /boot/grub/menu.lst to that effect. Eg, replace that section with (the lines starting with # are used the ones with ## are skipped)....[/QUOTE]

Cheers, but I also know that.

---

### Post by odysseus.lost on 2006-06-26
[QUOTE=thasheep]On ubuntu, runlevel 2 is default. This can be changed by modifying the line 'id:2:initdefault:' in /etc/inittab
However, this in itself won't do much, unless you change it to 1 (single user). As you might know, setting it to 0 (shutdown) or 6 (reboot) is stupid. By default 2-5 are all multi-user with gdm (X11). This can be changed. Eg to prevent X loading automatically on runlevel 4
```
sudo rm /etc/rc4.d/S??gdm
```If you're running kubuntu, it's probably kdm rather than gdm. The files in /etc/rc[runlevel].d/ are all symlinks to services (in /etc/init.d) to start when starting the runlevel have a look at 'ls -l /etc/rc?.d'. You can recreate the symlink by copying it from another runlevel or by doing ```
cd /etc/rc[runlevel].d
sudo ln -s ../init.d/[service_name] S[start_order][service_name]
```[/QUOTE]

Thanks this did the trick.... changed the default runlevel to 3 and deleted the gdm loader script from rc2.d...

Cheers thasheep.

---

