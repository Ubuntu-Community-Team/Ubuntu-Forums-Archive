---
title: "After kernel install, coretemp.2 folder missing"
date: 2010-11-24
forum: General Help
---

### Post by Cavsfan on 2010-11-24
I installed the 2.6.35-23-generic kernel yesterday and now conky doesn't run because there is a folder that is now missing.
Conky runs at startup and when entering this in terminal: **conky -c /home/cavsfan/.conkyrc**
I get this error 
```
Conky: can't open '/sys/bus/platform/devices/coretemp.2/temp1_input': No such file or directory
please check your device or remove this var from Conky
***** Imlib2 Developer Warning ***** :
	This program is calling the Imlib call:

	imlib_context_free();

	With the parameter:

	context

	being NULL. Please fix your program.
```

And sure enough folder coretemp.2 is missing: 
```
cavsfan@cavsfan-MS-7529:~$ cd /sys/bus/platform/devices/
cavsfan@cavsfan-MS-7529:/sys/bus/platform/devices$ ls
[color=#008080]coretemp.0  coretemp.3     Fixed MDIO bus.0  pcspkr
coretemp.1  f71882fg.2560  i8042             serial8250[/color]
cavsfan@cavsfan-MS-7529:/sys/bus/platform/devices$
```

Does anyone know how to get /sys/bus/platform/devices/coretemp.2/temp1_input back? 
The whole folder is missing and I have tried uninstalling lm-sensors, hddtemp without success.

I do not understand why the folder would be missing after an update. 
Thanks in advance! :D

---

### Post by Cavsfan on 2010-11-24
One of my quad core's temperature monitoring folders is missing for some odd reason.
It's is core number 3 and I have no idea how it came up missing or how I get the folder back.

I am hoping some one does.
Thanks!

---

### Post by Cavsfan on 2010-11-25
Does any one have a clue as how I get the folder back?
Thanks!

---

### Post by Cavsfan on 2010-11-28
Anybody have a clue how I get my folder back?
Thanks and I would be greatly indebted to anyone who can tell me how to fix this short of a clean install.

---

### Post by miegiel on 2010-11-28
Instead of
```
sudo apt-get remove lm-sensors
```
try
```
sudo apt-get purge lm-sensors
```
*Purge* also removes any configuration files.

---

### Post by Cavsfan on 2010-11-28
> **miegiel said:**
> Instead of
```
sudo apt-get remove lm-sensors
```try
```
sudo apt-get purge lm-sensors
```*Purge* also removes any configuration files.

Thanks, but I also tried that and it didn't bring back the missing folder. I have a bad feeling about this.  :sad: And installing 
or rather getting an update with a new kernel should not have caused this! Should I have not allowed the new kernel to 
be installed?

---

### Post by miegiel on 2010-11-28
> **Cavsfan said:**
> Thanks, but I also tried that and it didn't bring back the missing folder. I have a bad feeling about this.  :sad: And installing 
or rather getting an update with a new kernel should not have caused this! Should I have not allowed the new kernel to 
be installed?

The previous kernel should still be listed in the boot menu, you could try booting it and see if it solves the problem. If it does you have probably found a bug in the new kernel.

Alternatively you can check the sensor(s) listed in */etc/modules*, maybe there's a fault there.

---

### Post by Pablo Pablovski on 2010-11-28
I'd be tempted to reboot, selecting the last known "good" kernel from GRUB, use Synaptic to remove the latest kernel that seems to have caused tbe problem with sensors, reboot again and try re-installing the new kernel from Synaptic.

There are a few risks in doing that, so backup first.

---

### Post by Cavsfan on 2010-11-28
I have only the new kernel as the older one would give me nothing but a shell prompt to login. I purged lm-sensors 
and I am going to try to install the last 2 kernels and when all is good (hopefully) I will reinstall lm-sensors and run 
sensors-detect. When I ran sensors detect I did notice that it found a driver coretemp, which is what I am missing 
for the 3rd core.

I believe I will at least be able to get into recovery mode if all else fails and back stuff up.
Thanks for your help. It may 
be tomorrow before I am back up. Glad I have windows 7 to fall back on if I need to.

---

### Post by miegiel on 2010-11-28
I just installed the 2.6.36 kernel from [http://kernel.ubuntu.com/](http://kernel.ubuntu.com/) to see if it would solve some issues i'm having. Maybe it will solve your problem too.

Make a temporary directory (anywhere in your home), go to the directory in the terminal and do:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
sudo dpkg -i linux*.deb
```
That's for the 32bit kernel, replace *_i386.deb* with *_amd64.deb* for the 64bit kernel and don't forget you need the linux-headers-..._all.deb for both. (When you're done you can ditch the directory.)

---

### Post by Cavsfan on 2010-11-29
> **miegiel said:**
> I just installed the 2.6.36 kernel from [http://kernel.ubuntu.com/](http://kernel.ubuntu.com/) to see if it would solve some issues i'm having. Maybe it will solve your problem too.

Make a temporary directory (anywhere in your home), go to the directory in the terminal and do:
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-headers-2.6.36-020636_2.6.36-020636.201010210905_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.36-maverick/linux-image-2.6.36-020636-generic_2.6.36-020636.201010210905_i386.deb
sudo dpkg -i linux*.deb
```That's for the 32bit kernel, replace *_i386.deb* with *_amd64.deb* for the 64bit kernel and don't forget you need the linux-headers-..._all.deb for both. (When you're done you can ditch the directory.)


You are a genius!!! It worked like a charm! I was trying to install the older kernel and in recovery mode the conky worked and all of the core temps were there.
But, it would not come up in the regular mode.

I did what you said changing the lines for 64 bit and I seen it build my nvidia driver successfully and now my conky is back to normal!

So, is this kernel OK to keep using? That is probably a dumb question, but I don't have much knowledge about kernels. I just know frustration was setting in pretty bad.
Thanks!!! :D

---

### Post by miegiel on 2010-11-29
> **Cavsfan said:**
> You are a genius!!! It worked like a charm! I was trying to install the older kernel and in recovery mode the conky worked and all of the core temps were there.
But, it would not come up in the regular mode.

I did what you said changing the lines for 64 bit and I seen it build my nvidia driver successfully and now my conky is back to normal!

So, is this kernel OK to keep using? That is probably a dumb question, but I don't have much knowledge about kernels. I just know frustration was setting in pretty bad.
Thanks!!! :D

You're welcome :D

I'm no genius though, or else I would have solved my problem already. I just came across this way to get the next kernel trolling through the forums and since my problem also started after the latest kernel update I thought it might help me. It hasn't so far but I'll nail the problem sooner or later. Anyway, it reminded me of your problem and not being able to revert back to the older kernel, so I thought I should suggest the option here.

---

### Post by Cavsfan on 2010-11-30
I tried removing the last 2 kernels  (22 and 23) via these commands:
```
sudo apt-get purge linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic
```and then
```
sudo apt-get install linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic
```It was unusable before, but it built the nVidia video driver and when I booted into this kernel, everything looked good including conky!

I also tried the same thing with the 23 kernel and the conky still didn't work as the same directory was still missing.
So, I will remove the 23 kernel, keep the 22 kernel as my backup. Strange :? !

---

### Post by Cavsfan on 2010-11-30
Well I learned something. When I removed the middle kernel (23) of these three:

2.6.36-020636-generic
2.6.35-23-generic
2.6.35-22-generic

My custom grub menu would not pick the latest kernel (the top one). Apparently the custom grub menu entry from 
the tutorial in my sig. pulls the latest installed kernel and it could not find the 23 kernel as I had removed it. So, I had to 
re-install the 23 kernel.  Then I had to remove and re-install the 020636 kernel. Now my custom grub menu is happy and 
pulls that newest one in. This totally makes sense for the custom menu to work that way and I am glad I know that now.

Linux/Ubuntu is always a learning experience. If you know everything there is to know about everything in both, 
you are most probably just fooling yourself. I doubt the smartest person in the world knows everything about this stuff.
I could be wrong though and I definitely know that person is not me...

---

### Post by Cavsfan on 2010-12-13
```
sudo apt-get purge lm-sensors
```This command did not even get rid of the CPU temperature sensors. I executed that command and rebooted and the conky still came up 
just fine and the folders are all there on kernel 2.6.35-22-generic.

```
cavsfan@cavsfan-MS-7529:/sys/bus/platform/devices$ ls
[COLOR=RoyalBlue]coretemp.0  coretemp.2  f71882fg.2560     i8042   serial8250
coretemp.1  coretemp.3  Fixed MDIO bus.0  pcspkr[/COLOR]
cavsfan@cavsfan-MS-7529:/sys/bus/platform/devices$ 

```If lm-sensors does not install these temperature sensor folders, what does?
I have purged and reinstalled kernel 2.6.35-22-generic several times and it installs great and the conky runs great with the temps for all 4 cores.

But, when I purge and reinstall kernel 2.6.35-23-generic the coretemp.2 folder for the 3rd core is always missing and conky will not run.

I run sensors detect after installing lm-sensors and it finds coretemp drivers, but does anyone know what creates the folders in **/sys/bus/platform/devices** ?

---

### Post by Cavsfan on 2010-12-20
The 2.6.35-23-generic 64 bit kernel could just not be fixed to where the coretemp driver for the 3rd core would display the temp.
It would give conky an error and prevent it from running and in the sensors applet it would display an error for my 3rd core. I had 
to delete that.

Yesterday that 2.6.36-020636-generic kernel was doing some strange stuff and I had to remove it.

So, today I was able to get the 2.6.35-24-generic 64 bit kernel and everything is back to normal.

---

