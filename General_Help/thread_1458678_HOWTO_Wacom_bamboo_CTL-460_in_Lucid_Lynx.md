---
title: "HOWTO Wacom bamboo CTL-460 in Lucid Lynx"
date: 2010-04-20
forum: General Help
---

### Post by Lithium Rain on 2010-04-20
I thought I'd share how I got mine to work -   [[COLOR="Lime"]this guy[/COLOR]]("http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/") wrote an excellent howto - worked perfectly for me. I tried to make it work for hours on my own, but this worked like a charm. :guitar:

> The new Wacom Bamboo Pen (CTL-460) doesn’t work in Ubuntu Lucid out-of-the-box. You need a newer kernel module than the one that comes with Lucid by default. It’s pretty easy to get it working though, you just need to know how.

First, install some compiling tools and header files:
```
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
```

Next, download the latest linuxwacom driver (0.8.6 at the moment of writing):
```
wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
```

Now unpack, configure compile and install it:
```
tar -xf linuxwacom-0.8.6.tar.bz2
cd linuxwacom-0.8.6
./configure --enable-wacom
cd src/2.6.30/ 
```# I know this is the wrong version, but it's the highest available and it works
```
make
sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
sudo rmmod wacom
sudo modprobe wacom
```

The tablet should work now. You can also add the module name to /etc/modules to automatically load it on boot. 

He also says (and I can confirm) that the gray lines are the new borders of the tablet. A little annoying, but I imagine one could configure that, too.

---

### Post by iceland1209 on 2010-04-21
THANK YOU!

I am new to Ubuntu/Linux.  I spent countless hours trying to get my tablet to work.  Found your post and less than 10 minutes later - a big smile - my tablet works!
Thank You!

---

### Post by Lithium Rain on 2010-04-22
You're welcome! I'm very glad it helped. :-)

---

### Post by Sawer on 2010-04-22
I have a bamboo fun CTE 450/S it is working  only as a pointer. My question is how to I get to wacomcpl.
Thanks

---

### Post by Lithium Rain on 2010-04-25
Just type it in a shell.

---

### Post by pererik87 on 2010-05-01
Off course when i read this linuxwacom have deleted the file and changed everything. im on the last step. 

sudo rmmod
ERROR: Module wacom does not exist in /proc/modules
xxx@xxx-laptop:~/linuxwacom-0.8.6-1/src/2.6.30$ 

Any ideas??

---

### Post by bdvd on 2010-05-02
you are the best person eveeeer!, totally fix! :D!

---

### Post by bigfootffk on 2010-05-03
Thanks my bamboo tablet is working at last. I owe you a pint.:D

---

### Post by pererik87 on 2010-05-03
i so got totally nowhere after 3 hours :/

---

### Post by pererik87 on 2010-05-04
anyone that can upload  linuxwacom-0.8.6.tar.bz2 to this post because i cant get the 0.8.6-1.... to work at all. Ill owe you a pint

---

### Post by Balian on 2010-05-04
> **pererik87 said:**
> anyone that can upload  linuxwacom-0.8.6.tar.bz2 to this post because i cant get the 0.8.6-1.... to work at all. Ill owe you a pint
Have you downloaded 0.8.6-1?
If so just change 
```
tar -xf linuxwacom-0.8.6.tar.bz2
cd linuxwacom-0.8.6
```To
```
tar -xf linuxwacom-0.8.6-1.tar.bz2
cd -linuxwacom-0.8.6-1
```It worked for my CTH-460 Pen & Touch.

I also just got it to work on my dual monitor system with no problems.
You do need to add the word 'wacom' to the end of etc/modules for it work after you reboot.
```
sudo gedit /etc/modules
```

---

### Post by pererik87 on 2010-05-05
Thats what i did, but it failed. Might it work if i reinstall???

---

### Post by ctw on 2010-05-05
Hi!

I think with the new version 0.8.6-1 your Solution doesn't work, because when you try to compile, the first steep has no problems:

linuxwacom-0.8.6-1/src/2.6.30$ make
    Building linuxwacom drivers for 2.6 kernel.
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built
make -C /lib/modules/2.6.32-22-generic/build M=/home/catworld/Baixades/linuxwacom-0.8.6-1/src/2.6.30
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
catworld@catworld-XPC:~/Baixades/linuxwacom-0.8.6-1/src/2.6.30$ sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
cp: ha fallat stat() sobre «wacom.ko»: No such file or directory
catworld@catworld-XPC:~/Baixades/linuxwacom-0.8.6-1/src/2.6.30$ cd ..
catworld@catworld-XPC:~/Baixades/linuxwacom-0.8.6-1/src$ cd ..
catworld@catworld-XPC:~/Baixades/linuxwacom-0.8.6-1$ ./configure --enable-wacom
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gawk... (cached) gawk
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for HAL... no
checking for arch type... x86_64-linux-gnu
checking for kernel type... Linux
checking for linux-based kernel... yes
checking for kernel source/headers... /lib/modules/2.6.32-22-generic/build
checking kernel version... 2.6.32-22-generic
checking for kernel module support... yes
checking for Xlib... yes
checking for XSERVER... yes
checking for xserver libc-wrapper header-files... no
checking if scaling tablet to screen size is needed... no
checking if Xorg server is version 1.4 or later... yes
checking if Xorg is 7.3 or earlier... no
checking if Xorg server is version 1.5.2 or later... yes
checking if Xorg server is version 1.6 or later... yes
checking if Xorg SDK defined IsXExtensionPointer... yes
checking if Xorg SDK defines dixScreenOrigins... yes
checking XInput extension version... >= 2.0
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for tclsh... /usr/bin/tclsh
checking for tcl version... 8.4
checking for tcl header files... found, /usr/include/tcl8.4
checking for tk header files... found, /usr/include/tcl8.4
checking ncurses.h usability... yes
checking ncurses.h presence... yes
checking for ncurses.h... yes
checking if libwacomcfg should/can be built... yes
checking if libwacomxi should/can be built... yes
checking if wacdump should/can be built... yes
checking if xidump should/can be built... yes
checking if xsetwacom should be built... yes
checking if wacomxrrd should be built... checking X11/extensions/Xrandr.h usability... no
checking X11/extensions/Xrandr.h presence... no
checking for X11/extensions/Xrandr.h... no
checking for Wacom X driver module path... /usr/lib/xorg/modules/input
checking for dynamic driver loading support... yes
checking if wacom_drv.{o,so} should be compiled... yes
checking if gcc accepts -fno-merge-constants... yes
checking if gcc accepts -fno-stack-protector... yes

configure: creating ./config.status
config.status: creating Makefile
config.status: creating mkxincludes
config.status: creating src/Makefile
config.status: creating src/util/Makefile
config.status: creating src/xdrv/Makefile
config.status: creating src/2.6.9/Makefile
config.status: creating src/2.6.10/Makefile
config.status: creating src/2.6.11/Makefile
config.status: creating src/2.6.13/Makefile
config.status: creating src/2.6.14/Makefile
config.status: creating src/2.6.15/Makefile
config.status: creating src/2.6.16/Makefile
config.status: creating src/2.6.18/Makefile
config.status: creating src/2.6.19/Makefile
config.status: creating src/2.6.22/Makefile
config.status: creating src/2.6.24/Makefile
config.status: creating src/2.6.26/Makefile
config.status: creating src/2.6.27/Makefile
config.status: creating src/2.6.30/Makefile
config.status: creating src/wacomxi/Makefile
config.status: creating src/wacomxi/wacomcpl
config.status: creating src/include/xdrv-config.h
config.status: src/include/xdrv-config.h is unchanged
config.status: creating src/include/kernel-config.h
config.status: src/include/kernel-config.h is unchanged
config.status: creating src/include/util-config.h
config.status: src/include/util-config.h is unchanged
config.status: executing depfiles commands

----------------------------------------
  BUILD ENVIRONMENT:
       architecture - x86_64-linux-gnu
       linux kernel - yes 2.6.30
  module versioning - no 
      kernel source - yes /lib/modules/2.6.32-22-generic/build
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg
          XSERVER64 - yes
           dlloader - yes
               XLib - yes /usr/lib
         xf86config - no
                TCL - yes /usr/include/tcl8.4
                 TK - yes /usr/include/tcl8.4
            ncurses - yes

  BUILD OPTIONS:
            wacom.o - yes
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes
         libwacomxi - yes
          xsetwacom - yes
          wacomxrrd - no
              hid.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no
  wacom*_drv quirks - IsXExtensionPointer key-events dixScreenOrigins
----------------------------------------

but in the second steep, when you try to copy the "modul" it doesn't find:

linuxwacom-0.8.6-1/src/2.6.30$ ls
Makefile     modules.order   wacom.h      wacom_wac.c
Makefile.in  Module.symvers  wacom_sys.c  wacom_wac.h

/linuxwacom-0.8.6-1/src/2.6.30$ sudo cp wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/
cp: ha fallat stat() sobre «wacom.ko»: No such file or directory


Anybody can help us? TIA

---

### Post by jaxxed on 2010-05-05
to whoever asked for the source file, here's a link: [linuxwacom-0.8.6-1.tar.bz2/download]("http://sourceforge.net/projects/linuxwacom/files/linuxwacom/0.8.6-1/linuxwacom-0.8.6-1.tar.bz2/download")

ctw: it appears that you're actually using kernel 2.6.32, wheras the wacom source seems to only have code for up to 2.6.30.   I am in the same situation, and I'm trying to figure out if it's possible to cross compile.
I'd say that it's likely this is the soruce of your problem.  Do you have 2.6.30 on your machine?  If so you could try booting using that module, and then compiling, then rebooting into 2.6.33 and using the compiled 2.6.30 module.

I'll see if I can do it too.

---

### Post by opensource-for-all on 2010-05-06
> **pererik87 said:**
> Off course when i read this linuxwacom have deleted the file and changed everything. im on the last step. 

sudo rmmod
ERROR: Module wacom does not exist in /proc/modules
xxx@xxx-laptop:~/linuxwacom-0.8.6-1/src/2.6.30$ 

Any ideas??

The problem is that there is supposed to be a line between "sudo cp..." and "sudo rmmod wacom".  

[FONT=monospace][/FONT]After you do "sudo  cp wacom.ko /lib/modules/`uname  -r`/kernel/drivers/input/tablet", do:

sudo depmod -a

and continue on with sudp rmmod wacom and so on.

source: [http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-lucid-lynx-and-wacom-bamboo-ctl460/](http://nfolamp.wordpress.com/2010/05/02/ubuntu-10-04-lucid-lynx-and-wacom-bamboo-ctl460/)

Hope it helps.  I was having the same problem for some time too.

---

### Post by pererik87 on 2010-05-07
Thanks for the new ides guys ill try them when i get home. 

I recommend everyone to click the "this bug affects me" in this bug report [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/568064?comments=all](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/568064?comments=all)

---

### Post by Balian on 2010-05-07
I've just had to reinstall linuxwacom-0.8.6-1 again as I upgraded my kernal to 2.6.32-22, without any problems, I assume you have checked out this post: [http://ubuntuforums.org/showthread.php?t=1038949&highlight=wacom+bamboo](http://ubuntuforums.org/showthread.php?t=1038949&highlight=wacom+bamboo) Favux & Ayuthia are genius's when it comes to wacom. I hope you get it working, I can't imagine not having my wacom, it's one of the reasons I changed from Fedora to Ubuntu coz I could get it working.

---

### Post by opensourcenoob on 2010-05-28
I've tried these steps mentioned to get my Bamboo pen (newer edition) to work but im getting this error when i type the make command in the terminal. I am using the linuxwacom-0.8.6-2.tar.bz2 file.


make: *** No targets specified and no makefile found. Stop.


please shed some light on where im going wrong thanks for your patience

---

### Post by Favux on 2010-05-28
Hi opensourcenoob,

Welcome to Ubuntu forums! 

With 0.8.6-2 you no longer need the extra directory change 'cd src/2.6.30/'.  The config for 0.8.6-2 was fixed so it is now aware when Xserver 1.7 is present, and it excludes the wacom X driver so only the wacom.ko is in the config.in and compiled.

Hope this helps.

---

### Post by [mag] on 2010-06-07
Hi people :)

I have this weird problem. I'm using Ubuntu 10.04, and followed the relevant instructions to install version 0.8.6-1 of the linuxwacom driver, wacom.ko. To my delight, this made my Bamboo Pen&Touch work fairly well (except for some known issues). All well and good.

However, yesterday I discovered that it wasn't working anymore: With the tablet, I can not move the cursor in X or draw in the Gimp, the buttons have no effect, no actions show up in "xev", and "xsetwacom list dev" prints nothing. Something is working, however, since "dmesg" prints this when I reconnect the tablet:

> [ 3646.973882] usb 2-5.1.2: new full speed USB device using ehci_hcd and address 8
[ 3647.089543] usb 2-5.1.2: configuration #1 chosen from 1 choice
[ 3647.093909] input: Wacom BambooFun 2FG 4x5 Pen as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.1/2-5.1.2/2-5.1.2:1.0/input/input32
[ 3647.099787] input: Wacom BambooFun 2FG 4x5 Finger as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5.1/2-5.1.2/2-5.1.2:1.1/input/input33


It is attached the same way as always, and the LED on the tablet is showing off all its colors and intensities at the right times. The tablet is also working as before on my MacBook. In conclusion; this is not a hardware issue.

I have tried recompiling and reinstalling several different versions of wacom.ko (0.8.6-1, 0.8.6-2 and 0.8.7-2) and rebooting, with no effect.

I am pretty sure that I have the same kernel as before; 2.6.32-22.

So... any ideas? :)

---

### Post by Favux on 2010-06-07
Hi [mag],

Welcome to Ubuntu forums!

My guess is that you had a kernel update.  That will knock out a compiled wacom.ko because the new kernel has a new modules directory that the compiled wacom.ko isn't in.  So you can first try copying the compiled wacom.ko from the unpacked linuxwacom tar you used into place and if that fails recompile.  To tell what kernel you have in a terminal enter:
```
cat /proc/version_signature
```
That will get the last little suffix which can distinguish versions.

I'm not sure why your compiles aren't working.  Any errors?  Since 0.8.6-1 isn't available any longer you should be using 0.8.6-2, which was also the first version to be Xserver version aware.  In other words you no longer have to do the extra directory change with 0.8.6-2 (and up) like you did with 0.8.6-1.  Could that be why it isn't working?  Maybe if you aren't doing the extra directory change you're still using the modified copy command for the extra directory change instead of the normal one?:
```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

---

### Post by [mag] on 2010-06-08
**Update:** I got it working! See below.

> **Favux said:**
> Welcome to Ubuntu forums!

Thanks :)

> **Favux said:**
> To tell what kernel you have in a terminal enter:
```
cat /proc/version_signature
```
That will get the last little suffix which can distinguish versions.

My version signature is "Ubuntu 2.6.32-22.36-generic 2.6.32.11+drm33.2". Also, my architecture is x86-64.

> **Favux said:**
> I'm not sure why your compiles aren't working.  Any errors?

No errors, as far as I can tell. For all I know, this might not be a problem with wacom.ko at all.

> **Favux said:**
> ```
sudo cp ./src/2.6.30/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
```

So... is that the cp-command I am supposed to use? In that case I am using the correct one.

I've attached a dump of the terminal with the whole procedure. Maybe there's something there.

----

I do, however, get some errors in my /var/log/Xorg.0.log when plugging the Bamboo:

```

(II) config/udev: Adding input device Wacom BambooFun 2FG 4x5 Pen (/dev/input/mouse3)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Wacom BambooFun 2FG 4x5 Pen (/dev/input/event8)
(**) Wacom BambooFun 2FG 4x5 Pen: Applying InputClass "evdev tablet catchall"
(**) Wacom BambooFun 2FG 4x5 Pen: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(EE) module ABI major version (2) doesn't match the server's version (7)
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input/wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)
(EE) No input driver matching `wacom'
(II) config/udev: Adding input device Wacom BambooFun 2FG 4x5 Finger (/dev/input/mouse4)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Wacom BambooFun 2FG 4x5 Finger (/dev/input/event9)
(**) Wacom BambooFun 2FG 4x5 Finger: Applying InputClass "evdev touchpad catchall"
(**) Wacom BambooFun 2FG 4x5 Finger: Applying InputClass "touchpad catchall"
(**) Wacom BambooFun 2FG 4x5 Finger: Applying InputClass "Wacom class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.1
(EE) module ABI major version (2) doesn't match the server's version (7)
(II) UnloadModule: "wacom"
(II) Unloading /usr/lib/xorg/modules/input/wacom_drv.so
(EE) Failed to load module "wacom" (module requirement mismatch, 0)
(EE) No input driver matching `wacom'

```

I don't understand why there is a problem, though. My wacom_drv should be up to date, since I just did:

```

sudo apt-get purge xserver-xorg-input-wacom
sudo apt-get install xserver-xorg-input-wacom xserver-xorg-input-all

```

**Update:** Apparently, this reinstall of xserver-xorg-input-wacom was exactly what I needed. But I also needed to restart X afterwards to get it working. I have *no* idea what messed up my wacom_drv.so, though.

---

### Post by Favux on 2010-06-08
Outstanding!  :)

> I have no idea what messed up my wacom_drv.so, though.
Probably will remain a mystery.  Presumably something to do with the update, hopefully not a disk or RAM problem.
> But I also needed to restart X afterwards to get it working. 
Right, that's why after copying the wacom.ko into place and doing:
```
sudo depmod -a
```
I recommend rebooting.  I know you shouldn't have to but for whatever reason it seems to work better.  Otherwise there's a few that don't get the driver working.

---

### Post by [mag] on 2010-06-08
Thank you for your quick responses! Keep up the good work :)

---

### Post by opensource-for-all on 2010-06-16
Yeah, hi guys. The above method works, but after installing the driver, the pen acted weird. The mouse moves when I move my pen across the tablet, but would suddenly stop whenever I click something on the screen. Then it takes a while for it to be working again, and same thing happens every time I click on the screen. Anyone know what's wrong?

---

### Post by thunderdan on 2010-06-16
I get this:

```
daniel@daniel-desktop:~$ wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
--2010-06-16 02:24:18--  http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.6.tar.bz2
Resolving prdownloads.sourceforge.net... 216.34.181.59
Connecting to prdownloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-06-16 02:24:18 ERROR 404: Not Found.

daniel@daniel-desktop:~$
```

---

### Post by Favux on 2010-06-16
Hi opensource-for-all,

Check that the wacom drivers actually have your tablet by checking Xorg.0.log in /var/log.  It may be another driver like evdev.


Hi thunderdan,

Linuxwacom 0.8.6 is no longer posted at the LWP site.  You want 0.8.6-2.  See [post #1077]("http://ubuntuforums.org/showpost.php?p=9419773&postcount=1077") abstracted from the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

---

### Post by thunderdan on 2010-06-16
Thanks, Favux. I got 0.8.6-2. Now I'm to this part:
```
daniel@daniel-desktop:~/linuxwacom-0.8.6-2/src/2.6.30$ sudo cp wacom.ko /lib/modules/'uname -r'/kernel/drivers/input/tablet
[sudo] password for daniel: 
cp: cannot create regular file `/lib/modules/uname -r/kernel/drivers/input/tablet': No such file or directory
daniel@daniel-desktop:~/linuxwacom-0.8.6-2/src/2.6.30$ 

```

---

### Post by Favux on 2010-06-16
Hi thunderdan,

Can you tell me a little more about your system?  What release/kernel are you on, etc.?  And why did you make the directory change to /src/2.6.30?  Did you compile in that directory?

---

### Post by thunderdan on 2010-06-16
> **Favux said:**
> Hi thunderdan,

Can you tell me a little more about your system?  What release/kernel are you on, etc.?  And why did you make the directory change to /src/2.6.30?  Did you compile in that directory?

The release is lucid. The kernel is 2.6.32-22-generic. I changed directory to /src/2.6.30 because the first post of this thread said:

```
tar -xf linuxwacom-0.8.6.tar.bz2
cd linuxwacom-0.8.6
./configure --enable-wacom
cd src/2.6.30/
```

I'm not sure if I compiled in that directory or not. "make" is the command to compile, right? If so, then yes, I did compile in that directory.

But I noticed one thing I did wrong. I used ' instead of ` when typing `uname -r`. I just tried it with the correct ` and got no error message. Now when I moved on to the next line:

```
daniel@daniel-desktop:~/linuxwacom-0.8.6-2/src/2.6.30$ sudo rmmod wacom
ERROR: Module wacom does not exist in /proc/modules

```

---

### Post by Favux on 2010-06-16
OK, with 0.8.6-2 the extra directory change to src/2.6.30/ is unnecessary.  See post #21 above.  I think you're ok because it sounds like the wacom.ko was compiled and in /src/2.6.30.

Good catch on the `.

I would do 'depmod -a' and reboot.

---

### Post by thunderdan on 2010-06-16
> **Favux said:**
> OK, with 0.8.6-2 the extra directory change to src/2.6.30/ is unnecessary.  See post #21 above.  I think you're ok because it sounds like the wacom.ko was compiled and in /src/2.6.30.

Good catch on the `.

I would do 'depmod -a' and reboot.

It works! Thanks, Favux! :)

---

### Post by ripps818 on 2010-06-16
Hey guys, I’ve made a dkms packge that should allow people to build new wacom modules automatcially when new kernels are installed. I’d appreciate it people could test it for me.

```
sudo add-apt-repository ppa:ripps818/wacom
sudo apt-get update
sudo apt-get install wacom-dkms
```

---

### Post by scotty64 on 2010-07-03
> **ripps818 said:**
> Hey guys, I’ve made a dkms packge that should allow people to build new wacom modules automatcially when new kernels are installed. I’d appreciate it people could test it for me.

```
sudo add-apt-repository ppa:ripps818/wacom
sudo apt-get update
sudo apt-get install wacom-dkms
```

Ripps818: Your PPA saved my day! After trying for hours to get the wacom stuff going I installed your wacom-dkms on two machines and my Wacom Bamboo Fun Pen & Touch worked out of the box (all functions). I only had to load the wacom module manually, but this is no big problem.
Thanks for your contribution, have some :popcorn: !

---

### Post by jrierab on 2010-07-12
> **ripps818 said:**
> 
```
sudo add-apt-repository ppa:ripps818/wacom
sudo apt-get update
sudo apt-get install wacom-dkms
```

Thank you! Works very well. It can't be more easy!

---

### Post by thetaz_x on 2010-07-27
Regards to making my tablet work upon startup.

It says do a "sudo gedit /etc/modules"
I've done many versions of this gksudo blah blah
I've tried : vim, kate, genie, gedit.

None of them can detect the character encoding.

Ideas on how to actually edit this file?

---

### Post by spaceshipguy on 2010-08-27
> **ripps818 said:**
> Hey guys, I’ve made a dkms packge that should allow people to build new wacom modules automatcially when new kernels are installed. 

```
sudo add-apt-repository ppa:ripps818/wacom
sudo apt-get update
sudo apt-get install wacom-dkms
```

Thank you! Thank you! Thank you!
For me, your code just worked.:D

---

### Post by misterbiskits on 2010-09-23
**ripps818 **this does not work for me.
I install the tablet as per page 1, using linuxwacom-0.8.8-8.tar.bz2, tablet begins working.
I install the update as shown above, tablet continues working.
Everything works fine until I shutdown, or logoff, at which point my computer freezes and I have to hard reboot.
After that ubuntu will not boot up, just freezes (blank screen) before the login screen.
So I did a format and clean install of ubuntu 10.04, install all updates, install tablet and update as above, same thing frozen blank screen at log off/shut down.
I am a newb.

---

### Post by jetblackstar on 2010-10-28
misterbiskits:
I don't know if you have made a /usr/lib/X11/xorg.conf.d/10-wacom.conf as part of your install steps, but when i was messing around with mine I managed to get the exact behaviour you described.

In my case it was a typo preventing X from starting up properly.  I had to SSH in from another box and "#" out all the bits id messed with.  
Apparently Ubuntu/Ludic is slightly crueller and unforgiving of ballsed up X configs. Fedora at least give you the Basic TTY terminal :P

If you get this again I can suggest you move or remove that file temporarily until you figure out what is wrong with it. Which while drastic is far less so than a reinstall.

This all said, your issue may be very different from mine :) 
Jet

---

### Post by jetblackstar on 2010-10-28
Got my Bamboo pen & touch "working" but Touch doesn't click when I tap. And when you try any of the buttons It pulls the cursor to the top left and clicks the Applications button.

Any ideas? Are other peoples Touch features working as expected? 
I'm guessing ive got an X Config setup wrong or something along those lines.

Thanks In advance.

---

### Post by Favux on 2010-10-28
Hi jetblackstar,

See the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

