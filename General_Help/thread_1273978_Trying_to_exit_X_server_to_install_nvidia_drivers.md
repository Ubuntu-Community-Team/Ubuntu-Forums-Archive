---
title: "Trying to exit X server to install nvidia drivers"
date: 2009-09-24
forum: General Help
---

### Post by hooberman on 2009-09-24
Hi,
I am trying to exit my X server so that I can install nvidia drivers for my new graphics card (I have Ubuntu 8.04). I have tried Ctl+Alt+F1, but this only gives a window which says "Computer running on AC power." I have also tried Ctl+Alt+FX where X=2-12, but this does nothing. Typing 'sudo /etc/init.d/gdm stop' gives:
 
*Starting anac(h)ronistic cron anacron [OK]
*Starting deferred execution scheduler atd [OK]
*Starting periodic scheduler crond [OK]
*Checking battery state... [OK]
*Running local boot scripts (/etc/rc.local) [OK]
 
at which point the system hangs and I need to use Ctl+Alt+Del to shut down. Finally, I have tried editing the runlevel in /etc/inittab but this file does not exist. 
 
This is driving me crazy- can anyone help?
Ben

---

### Post by nikhilk on 2009-09-24
No need to change the default runlevel. From a terminal execute
```
sudo init 1
```
That should give you a single user text terminal without any GUI.

---

### Post by hooberman on 2009-09-24
Hi Nikhilk,
  Thanks for getting back to me. I tried 'sudo init 1' and then chose root to get a command line prompt. When I try to install the drivers the installer complains that I am in runlevel 1 but should be in runlevel 3, and that this may cause problems. The installer then fails with the following output in the log file:

Using: nvidia-installer ncurses user interface
-> You appear to be running in runlevel 1; this may cause problems.  For exampl
   e: some distributions that use devfs do not run the devfs daemon in runlevel
   1, making it difficult for `nvidia-installer` to correctly setup the kernel 
   module configuration files.  It is recommended that you quit installation no
   w and switch to runlevel 3 (`telinit 3`) before installing.
   
   Quit installation now? (select 'No' to continue installation) (Answer: No)
-> License accepted.
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?]("ftp://download.nvidia.com%29?") (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com]("http://www.nvidia.com").

Any ideas?
Ben

---

### Post by nikhilk on 2009-09-24
I am not sure what instructions you are following for installing Nvidia drivers.
See if [these]("http://www.psychocats.net/ubuntu/nvidia") instructions work for you.

---

### Post by hooberman on 2009-09-24
I tried to follow these instructions. Under System>Administration>Hardware drivers there are no drivers listed and the window states "No proprietary drivers are in use on this system."

Arg!

---

### Post by nikhilk on 2009-09-25
Sorry, I do not have much experirence in this area as I have never had an Ubuntu machine with an Nvidia GPU. Maybe someone else will be able to help?

---

### Post by alphaniner on 2009-09-25
I'm running 9.04 and I installed the nVidia drivers through System->Administration->HW Drivers so I can't offer any specific help.  What I can point out is this:

> ERROR: Unable to connect to download.nvidia.com (unknown host)

How do you configure your network?  If you use Network Manager, you probably weren't connected to the internet in rl 1.

> ERROR: You do not appear to have libc header files installed on your system.

I think you need to install the package 'libc6-dev' to resolve this error.  You may also need a few other packages though, like 'build-essential'.

---

### Post by 3rdalbum on 2009-09-25
You need to install the "build-essential" package, and the linux-headers package that corresponds to your kernel (I can't remember the exact package name on 8.04).

---

