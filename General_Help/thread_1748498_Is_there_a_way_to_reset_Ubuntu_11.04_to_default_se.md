---
title: "Is there a way to reset Ubuntu 11.04 to default settings?"
date: 2011-05-03
forum: General Help
---

### Post by Mudi_ on 2011-05-03
Hi guys,
I recently installed the new 11.04 release and was messing around with the Compiz settings on Ubuntu Classic. I tried logging on to regular Ubuntu and everything crashed. When I start up there is no log in screen, only text shows. (I enter my log in information then type 'startx' in the terminal to show my desktop.) 
The desktop shows a messed up version of my custom configuration with Cairo-Dock all weird and everything in the wrong place. Also my custom start-up screen that I installed is distorted, and the GRUB screen shows up in purple. 

I was wondering if there was a way to reset Ubuntu 11.04 to the default settings? I tried typing 'unity --reset' in the terminal but it gets stuck at the line 'Setting Update "fullscreen_visual_bell"'.

Any help would be appreciated, thanks in advance.

---

### Post by sdowney717 on 2011-05-03
since all the user configuration is contained in each user home folder, then try making a new user and logging into the new user.
you can make a user from the commandline if the gui is shot.

---

### Post by notoriousdbp on 2011-05-03
You could re-install from live cd, if you have a separate /home partition you can do so with no data loss and it will probably be quicker than resetting things manually.

---

### Post by Peter09 on 2011-05-03
try

```
unity --reset
```

---

### Post by Mudi_ on 2011-05-03
Ok I managed to get the GUI working, but every time I open a window, it is blank. In order to see something I have to resize it through trial and error until it displays something. Usually the screen is very small. Also Ubuntu is very slow. Also some error messages keep popping up in the top right corner saying some plugins are missing/disabled. How do I fix this?

---

### Post by Peter09 on 2011-05-04
Sounds like an issue with your graphics card/driver.
What card have you got?

```
lshw -C video
```

---

### Post by Mudi_ on 2011-05-07
> **Peter09 said:**
> Sounds like an issue with your graphics card/driver.
What card have you got?

```
lshw -C video
```

PCI (sysfs)  
  *-display               
       description: VGA compatible controller
       product: C51 [GeForce 6150 LE]
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:fc000000-fcffffff memory:e0000000-efffffff memory:fb000000-fbffffff memory:80000000-8001ffff


Sorry for the late reply, I haven't been on Ubuntu in a while because I need to do assignments for school.

---

### Post by drewnoakes on 2011-05-10
> **Peter09 said:**
> try

```
unity --reset
```

This worked wonders for me.  Thanks very much.

A quick note to other newbies (like me) who may have tweaked their compiz settings too far and ended up with a blank screen... pressing Ctrl+Alt+F2 dropped me straight into a terminal where I could log in an issue this command.

---

### Post by Blasphemist on 2011-05-10
Try this to install the current Nvidia proprietary drivers.
> nVidia Driver
The current proprietary nVidia drivers are automatically installed using:
Menu -> System -> Administration -> Hardware Drivers
Look for the current drivers to activate there.
Here are alternate manual instructions.
Please make a backup of xorg.conf before following this method.
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
Install the nvidia-settings package:
 sudo apt-get install nvidia-settings
Download the nVidia driver:
wget -O NVIDIA-Linux-x86-pkg1.run [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
sudo sh NVIDIA-Linux-x86-pkg1.run
and choose yes to any verbose response. After you install the driver, reboot your computer.

---

### Post by $uraj on 2011-06-12
> **Peter09 said:**
> try

```
unity --reset
```
@Peter09

Wow.. the command worked.. My unity is reset now to default :) Thanks Peter09

---

