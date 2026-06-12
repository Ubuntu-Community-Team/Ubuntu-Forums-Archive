---
title: "Unable to find the kernel source tree Nvidia Driver Install"
date: 2010-05-12
forum: General Help
---

### Post by MasterShihoChief on 2010-05-12
So after getting around the Fakeraid bug, and the grub bug, and all the other bugs killing my system fixed and then i moved on to install my video driver.

There was nothing in Administration>Hardware Drivers, so i downloaded the latest driver for my two 8600m gt cards. Did the whole ctrl+alt+f2 and then stopping xserver and then running the driver install only to run into yet another damn bug(see log below)

I have tried fixing it by doing what other threads have said to do e.g:[http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia]("http://ubuntuforums.org/showthread.php?t=813931&highlight=nvidia") still nothing. 

I would really appreicate some help this time so i dont have to spend days trying to figure this out alone(which i doubt will happen, i don't have the slightest idea what to do on this one). 

Below is the Nvidia log.

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Thu May 13 03:14:33 2010
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 195.36.24.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel and that they are properly configured; on Red Hat Linux systems,
       for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
       installed.  If you know the correct kernel source files are installed,
       you may specify the kernel source path with the '--kernel-source-path'
       command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by koanhead on 2010-05-13
sudo apt-get install linux-source

should install the kernel source tree. If you have installed it already, Synaptic should be able to tell you the path to which it is installed (should be /usr/src/linux afaik).

---

### Post by koanhead on 2010-05-13
Ok, I just installed it myself, it installs a .tar.bz2 image which you will need to untar before the installer can find it. I used sudo file-roller for this.

---

### Post by MasterShihoChief on 2010-05-13
ok i hate to sound like an idiot i used the command to tell it where that untarballed folder is and the following spit out. Also that is not my kernel version. I have 2.6.31-21-generic and the files are for 2.6.32, is this the reason for the problem?


Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 195.36.24.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Using the kernel source path '/usr/src/linux-source-2.6.32' as specified by
   the '--kernel-source-path' commandline option.
ERROR: The kernel header file
       '/usr/src/linux-source-2.6.32/include/linux/version.h' does not exist. 
       The most likely reason for this is that the kernel source files in
       '/usr/src/linux-source-2.6.32' have not been configured.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by MasterShihoChief on 2010-05-13
bump

---

### Post by MasterShihoChief on 2010-05-14
bump ¬¬

---

### Post by MasterShihoChief on 2010-05-15
Ffs bump!!!!!1

---

### Post by MasterShihoChief on 2010-05-16
Wow would you look at that 4 days and I'm still using a broken OS, how about helping me solve this ¬¬

---

### Post by MasterShihoChief on 2010-05-17
bump? anyone?

---

### Post by 2hot6ft2 on 2010-05-17
We think we found the fix for nvidia.
First if using 64 bit you want to install the driver using the 2.6.32-21 kernel NOT the -22 kernel. We have tried pretty much every fix we could find and this one is looking like the best one yet.

So here's the fix.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112](http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112)

Replace the 2.6.32-22 kernel with the server kernel
```
sudo apt-get purge linux-headers-2.6.32-22 linux-image-2.6.32-22-generic
```
when that finishes install the server kernel per Blackwolfs's instructions
```
sudo apt-get install linux-headers-server linux-image-server linux-server
```
You will have to reboot after it finishes.
That's it.
Let us know if it works or not for you, so far we're getting good results and we want this bug squashed.
:guitar:

---

### Post by MasterShihoChief on 2010-05-17
Still doesnt work, this is getting quite frustrating. I did as u said and when it prompted me to choose an option for my current grub config i told it to keep the local copy (since i have edited it already for windows 7 *i have fake raid). I rebooted into it, i did a uname -r and got the Kernel version 2.6.32-22 generic. So i went to install the nvidia driver and still get the following error in nvidia.

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 195.36.24.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
ERROR: Unable to find the kernel source tree for the currently running kernel. 
Please make sure you have installed the kernel source files for your
kernel and that they are properly configured; on Red Hat Linux systems,
for example, be sure you have the 'kernel-source' or 'kernel-devel' RPM
installed. If you know the correct kernel source files are installed,
you may specify the kernel source path with the '--kernel-source-path'
command line option.
ERROR: Installation has failed. Please see the file
'/var/log/nvidia-installer.log' for details. You may find suggestions
on fixing installation problems in the README available on the Linux
driver download page at [www.nvidia.com](www.nvidia.com).

So i ran the commands again to uninstall the kernel incase i dont know maybe something messed up. So i uninstalled it and went to reinstall it and guess what i got. Terminal hangs at unpackaging the package. I let it run anyways and after 10minutes it says it installs. Now it says the kernel version is 2.6.31-21-generic. Im so confused >_<

So now i have no idea what to do, maybe i should just format and reinstall 9.10? Any help would be greatly appreciated

edit: i ran recovery mode and selected fix broken packages. Now it says i have 2.6.31.21 generic but when i try to remove it it says it doesnt exist. 

mastershihochief@cortanamobile:~$ sudo apt-get purge linux-headers-2.6.31-21 linux-image-2.6.31-21-generic
[sudo] password for mastershihochief: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.31-21
mastershihochief@cortanamobile:~$ uname -r
2.6.31-21-generic
mastershihochief@cortanamobile:~$ 

so at this point i really need some help, i cant keep using this broken os. Windows 7 is broken due to smart error on one of the disks so maybe thats what wrong here, who knows, i cant use that os either. Should i just reformat to 9.10 since 10.04 still has the fakeraid bug, and then upgrade, then run this again, and then see if nvidia installs or what. I need my computer badly right now and ubuntu is just not working >_<

---

### Post by 2hot6ft2 on 2010-05-17
Trying to install it on the 2.6.32-22 kernel is like beating your head against a wall. You'll get a headache but you wont make any progress.
If you reinstall and then don't even boot to the 2.6.32-22 kernel and choose the 2.6.32-21 kernel you'll do a whole lot better.

Ok, The 32 bit does NOT come with kernel 2.6.32-22 kernel at all, it was slipped in at the last minute and at the time of release it was not even a mainline kernel. It should NOT have been there.

Once you've made a lot of changes there's very little chance you'll ever get it straightened out without reinstalling.

Once you install the nvidia driver to the 2.6.32-21 kernel and you get rid of the 2.6.32-22 kernel and install the server kernel you will have both the 2.6.32-21-generic kernel and a 2.6.32-22-server kernel and they should both work with the nvidia driver.

Re-installing takes about 30 minutes or less, then you have a clean slate to fix it, as opposed to hours or days trying to undo the failed attempts.

It's your choice, all I can do is let you know what's working for others that have tried all kinds of things, myself included. I'm running the 32 bit with a nvidia driver right now.
:popcorn:

---

### Post by MasterShihoChief on 2010-05-18
I have 64 bit but i cant even get the correct kernel installed for it. its stuck on


2.6.**31**-21-generic

I cant even get any other kernel to install anymore i either get errors about the files not being available, or it says it does it and then it doesnt exist and it isnt running that version, or it just gives me the middle finger and says no cant install cuz it hangs at unpacking and crashes terminal. This is why i am wondering do i need to reinstall cuz ive screwed it up to much to be salvaged or is there a way to get to get to this 2.6.**32**-21 generic or server or w.e kernel version it is(so many version numbers being thrown around now i dont know which one is the broken one and which one is the one that works) so i can install the nvidia drivers

---

### Post by MasterShihoChief on 2010-05-18
Here i have uploaded what synaptic shows as installed images. Do i just remove them all and install the one you say? or do it a different way?

---

### Post by jocko on 2010-05-18
> **MasterShihoChief said:**
> I have 64 bit but i cant even get the correct kernel installed for it. its stuck on


2.6.**31**-21-generic

I cant even get any other kernel to install anymore i either get errors about the files not being available, or it says it does it and then it doesnt exist and it isnt running that version, or it just gives me the middle finger and says no cant install cuz it hangs at unpacking and crashes terminal. This is why i am wondering do i need to reinstall cuz ive screwed it up to much to be salvaged or is there a way to get to get to this 2.6.**32**-21 generic or server or w.e kernel version it is(so many version numbers being thrown around now i dont know which one is the broken one and which one is the one that works) so i can install the nvidia drivers
Looks like your upgrade from karmic failed and left your system with the old kernel.
Try to let the upgrade complete by running these commands in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux linux-headers-generic ubuntu-minimal ubuntu-standard ubuntu-desktop
```
If there are any errors, copy/paste them here.

---

### Post by jocko on 2010-05-18
> **MasterShihoChief said:**
> Here i have uploaded what synaptic shows as installed images. Do i just remove them all and install the one you say? or do it a different way?
Why do you have a server kernel installed? Server kernels are optimized for running on servers, and are probably not a good idea on a desktop.
Run the commands from my previous post. That will install the generic kernel, which is the best one for a desktop system. Then reboot and make sure you boot from the lucid kernel (2.6.32, and the -generic one, not the -server), not the old karmic kernel (2.6.31). If you don't see any boot menu on startup, press down the shift button during the bios tests and keep it pressed until you see the boot menu.
Once it's booted, open up synaptic and uninstall the karmic kernel as well as the server kernel.

---

### Post by 2hot6ft2 on 2010-05-18
The server kernel works with the nvidia drivers.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112](http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112)

---

### Post by MasterShihoChief on 2010-05-18
OK scratch everything. I installed linux-image 2.6.32-21-generic
Once again i told it to save save my local grub config.

It then hit me that grub never updated so i went in and manually reconfigured grub (it still had ubuntu 9.10 and the old kernel as the only boot method. I changed the path to this newly installed kernel and presto


mastershihochief@cortanamobile:~$ uname -r
2.6.32-21-generic
mastershihochief@cortanamobile:~$ 

I have regained my 1920x1200 resolution. Hardware drivers still says that no propriatary drivers are in use. The nvidia package still says cant find kernel source tree and the nvidia xorg control panel thingy is not installed. So now that i got this thing on the right kernel and back to its native resolution, how do i get the 195.36.24 driver installed so i can turn on desktop effects and be able to run wine programs.

ahh saw the post after i posted this. I will edit the bootloader again to boot from the server 32-22 image brb.

---

### Post by jocko on 2010-05-18
> **2hot6ft2 said:**
> The server kernel works with the nvidia drivers.
[http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112](http://ultimateeditionoz.com/forum/viewtopic.php?f=69&t=1112)
So does the -generic kernel. Trust me. I've never had any problems with the nvidia driver on either the -generic or -preempt kernels, and I've tried every kernel from lucid alpha 2 until the current kernel. There is no reason to run a server kernel on a desktop computer.

---

### Post by jocko on 2010-05-18
> **MasterShihoChief said:**
> OK scratch everything. I installed linux-image 2.6.32-21-generic
Once again i told it to save save my local grub config.

It then hit me that grub never updated so i went in and manually reconfigured grub (it still had ubuntu 9.10 and the old kernel as the only boot method. I changed the path to this newly installed kernel and presto


mastershihochief@cortanamobile:~$ uname -r
2.6.32-21-generic
mastershihochief@cortanamobile:~$ 

I have regained my 1920x1200 resolution. Hardware drivers still says that no propriatary drivers are in use. The nvidia package still says cant find kernel source tree and the nvidia xorg control panel thingy is not installed. So now that i got this thing on the right kernel and back to its native resolution, how do i get the 195.36.24 driver installed so i can turn on desktop effects and be able to run wine programs.

ahh saw the post after i posted this. I will edit the bootloader again to boot from the server 32-22 image brb.
Still, no need to run the server kernel.
If the driver manager does not pick up your nvidia card, just install the packages yourself:
```
sudo apt-get install nvidia-current
sudo nvidia-xconfig --force-generate
```

---

### Post by 2hot6ft2 on 2010-05-18
> **jocko said:**
> So does the -generic kernel. Trust me. I've never had any problems with the nvidia driver on either the -generic or -preempt kernels, and I've tried every kernel from lucid alpha 2 until the current kernel. There is no reason to run a server kernel on a desktop computer.
Then please explain to everyone with problems installing nvidia drivers that it works just fine and what everyone is doing wrong. I'll look in tomorrow to see what it is.
:popcorn:

---

### Post by MasterShihoChief on 2010-05-18
none of this is working. I have tried all kernels mentioned including server and generic. I have tried to post the 

> Still, no need to run the server kernel.
If the driver manager does not pick up your nvidia card, just install the packages yourself:
Code:
sudo apt-get install nvidia-current
sudo nvidia-xconfig --force-generate

This didnt do anything, it installed it, but it still shows nothing in the hardware drivers being used, and the 
Nvidia x server settings in the admin menu that just showed up says You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

i ran the nvidia xconfig and restarted x and i also get this error about unable to load nvidia module and ubuntu is now running in low graphics mode >_<, luckily i just restored the x.conf from backup and i dont ahve to deal with crap resolution again, but the drivers obviously wont install.

tried installing from the run pkg and still get the cant find kernel source tree for the current kernel error. anymore ideas?

---

### Post by MasterShihoChief on 2010-05-18
I am happy to announce that the problem is solved and i am running the current drivers. In addition to the grub problem and the kernel problem, i also needed the generic headers to be installed for and running from inside that exact kernel version. I am now running latest drivers on 2.6.32-22 generic with no problems so far. Thanks so much for everyones help ^^

---

### Post by jocko on 2010-05-18
> **MasterShihoChief said:**
> none of this is working. I have tried all kernels mentioned including server and generic. I have tried to post the 


This didnt do anything, it installed it, but it still shows nothing in the hardware drivers being used, and the 
Nvidia x server settings in the admin menu that just showed up says You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

i ran the nvidia xconfig and restarted x and i also get this error about unable to load nvidia module and ubuntu is now running in low graphics mode >_<, luckily i just restored the x.conf from backup and i dont ahve to deal with crap resolution again, but the drivers obviously wont install.

tried installing from the run pkg and still get the cant find kernel source tree for the current kernel error. anymore ideas?
I have no idea what could be causing your problems. If you are running the latest -generic kernel and have the corresponding kernel headers installed, I don't see why it would not work.
If I was having your problem I would do a clean reinstall of lucid and start over. That's probably faster and easier than trying to fix your current install (unless someone else here **know** what causes it and how to fix it).

---

### Post by 2hot6ft2 on 2010-05-18
> **jocko said:**
> I have no idea what could be causing your problems. If you are running the latest -generic kernel and have the corresponding kernel headers installed, I don't see why it would not work.
If I was having your problem I would do a clean reinstall of lucid and start over. That's probably faster and easier than trying to fix your current install (unless someone else here **know** what causes it and how to fix it).
Perhaps this will give you better understanding. If you're not familiar with the players in this conversation and how they fit in try googling them.
Messages back and forth about nouveau with Linus Torvalds.
A sneak peek dated Thu, 4 Mar 2010
> > *NOTE* in case you missed it: this will *break* your nvidia machine, its purely
> intentional. Rawhide should have the libdrm and driver updates necessary.

The rest is here: [http://lkml.org/lkml/2010/3/4/305](http://lkml.org/lkml/2010/3/4/305)
:(

---

### Post by jocko on 2010-05-19
> **2hot6ft2 said:**
> Perhaps this will give you better understanding. If you're not familiar with the players in this conversation and how they fit in try googling them.
Messages back and forth about nouveau with Linus Torvalds.
A sneak peek dated Thu, 4 Mar 2010

The rest is here: [http://lkml.org/lkml/2010/3/4/305](http://lkml.org/lkml/2010/3/4/305)
:(
That's got nothing to do with the op's problem. As you can see he managed to solve it by first making sure he booted from the lucid kernel instead of the old karmic kernel, then installing the kernel headers (which is pretty much what I said in my post).

> **jocko said:**
> **If you are running the latest -generic kernel and have the corresponding kernel headers installed, I don't see why it would not work.**

---

### Post by jcanini on 2010-05-23
I have being having the exact same problem.
The Nvidia installer not finding the kernel source.
After reading this thread it finally clicked that grub was still pointing to the old kernel.
Edited grub to boot to current kernel ( /boot/menu.lst )
Rebooted
Ctrl+Alt+F1 ### to go to terminal
sudo /etc/init.d/kdm stop ### to stop display manager, gdm stop for gnome
./Nvidia*         ### ran the nvidia installer downloaded from nvidia site.

And presto now have twin monitors running at hi res and 3d.
Such a simple thing to solve but I had missed it for ages.
Thanks to everyone who posted in this thread.
I am very happy not to have had to re-install as I cant remember the last time I had to do this to any of my machines running k/ubuntu and hope to keep this situation going.

---

