---
title: "Unable to install Nvidia drivers :("
date: 2005-02-07
forum: General Help
---

### Post by membreya on 2005-02-07
I'm trying to get the nvidia drivers up and running..found about as much "general" help as I can on the internet ...

But now my problem becomes specific (I've found responses but they're in German)

When I'm trying to install the nvidia drivers by doing a sudo sh -i NVIDIA-Linux-x86_64-1.0-6629-pkg2.run I'm getting:

> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Feb  8 01:48:44 2005

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  no precompiled interface: false
  no ncurses color        : false
  query latest driver ver : false
  OpenGL header files     : false
  no questions            : false
  silent                  : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : /usr/X11R6
  OpenGL install prefix   : /usr
  compat32 install prefix : /emul/ia32-linux
  installer install prefix: /usr
  utility install prefix  : /usr
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : /usr/src/linux-source-2.6.8.1
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com](ftp://download.nvidia.com))? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Using the kernel source path '/usr/src/linux-source-2.6.8.1' as specified by
   the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-source-2.6.8.1'
-> Performing CC test with CC="cc".
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the appropriate nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com). 

I'm currently running the 2.6.8.1-4-amd64 kernel and I've downloaded and extracted the 2.6.8.1 source code.

Any suggestions?  :confused:

---

### Post by mendicant on 2005-02-07
Any reason you're not using the .deb package?  You also don't usually want the source code, but the headers package.

---

### Post by friez on 2005-02-07
you have to config and build the kernel source in order to use the nvidia driver :sad: 
try installing nvidia-glx thought apt instead easier to manage that way 8)

edit: installing the right header files might due just as well :-#
edit 2 :mrgreen:  this is a howto that may help [http://ubuntuforums.org/showthread.php?t=12823](http://)

---

