---
title: "NVidia Graphics"
date: 2011-10-14
forum: General Help
---

### Post by tommy2k10 on 2011-10-14
My graphics card is an NVidia GeForce 6100.  I have got Ubuntu 11.10 32-bit.  
I have downloaded the Linux driver, but when I run it, it says I have got to disable X.
I have used stop commands for gdm, which it doesn't recognise, and lightdm, which turns the display off!! (and the system!)
It is also not included with the OS.

---

### Post by sgage on 2011-10-14
> **tommy2k10 said:**
> My graphics card is an NVidia GeForce 6100.  I have got Ubuntu 11.10 32-bit.  
I have downloaded the Linux driver, but when I run it, it says I have got to disable X.
I have used stop commands for gdm, which it doesn't recognise, and lightdm, which turns the display off!! (and the system!)
It is also not included with the OS.

When you say you've downloaded the Linux driver, do you mean you downloaded the install script from nvidia? If so, you must boot into rescue mode and install from there.

But did you try jockey-gtk? That's the easiest way to do it, and you get the Ubuntu tested package.

---

### Post by WasMeHere on 2011-10-14
Hi tommy2k10,

I guess that you have been running previous Ubuntu version on the same computer.

Do you know that you need that driver? Or would it be good enough to have the proprietary nvidia driver, that will be offered to you automatically a few minutes after you have started your new system?

Because it is a little complicated to install it (as you have already noticed).

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Dans564 on 2011-10-14
There is no reason to install using the download from the nvidia website.  It is overly complicated for a "nooby" linux user (I mean no disrespect. I have been using linux for 3.5 years and I still consider myself a noob :))  Use the additional Drivers app that is included with ubuntu.  It will pick the right proprietary driver and do all the dirty work for you

---

### Post by sgage on 2011-10-14
> **Dans564 said:**
> There is no reason to install using the download from the nvidia website.  It is overly complicated for a "nooby" linux user (I mean no disrespect. I have been using linux for 3.5 years and I still consider myself a noob :))  Use the additional Drivers app that is included with ubuntu.  It will pick the right proprietary driver and do all the dirty work for you

I don't know how exposed "additional drivers" is in Lubuntu (jockey-gtk IS 'additional drivers). You can launch it from a command line if you can't find it presented in a menu or whatever Lubuntu does.

---

### Post by tommy2k10 on 2011-10-17
> **sgage said:**
> When you say you've downloaded the Linux driver, do you mean you downloaded the install script from nvidia? If so, you must boot into rescue mode and install from there.

Yes I did try and install the script from nVidia.

But did you try jockey-gtk? That's the easiest way to do it, and you get the Ubuntu tested package.

No I haven't.  I'll have to look up how to use that!

---

### Post by tommy2k10 on 2011-10-17
I'm using it because, although it says it is 1024 x 768, the display still seems a bit too big!

---

### Post by WasMeHere on 2011-10-17
> **tommy2k10 said:**
> I'm using it because, although it says it is 1024 x 768, the display still seems a bit too big!

Please describe in detail what driver you are using! And what is the output of
```
xrandr
```
Can you change the graphic resolution with xrandr?
(See **man xrandr**)

We need some information to know where to start helping you :-)

---

### Post by tommy2k10 on 2011-10-17
This is copied from lshw in a Terminal:

description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi vga_controller bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:21 memory:f8000000-f8ffffff memory:e0000000-efffffff memory:fb000000-fbffffff memory:80100000-8011ffff

---

### Post by WasMeHere on 2011-10-17
I have an nvidia 430 card running with Ubuntu Studio 11.04 and it runs well. I suspect that it is a problem of the bleeding edge version 11.10. It should be resolved within a couple of weeks (so install the updates regularly).

Did you try the following command: **xrandr**

I suggest that you try different screen resolutions to check if some of them work better?

---

### Post by tommy2k10 on 2011-10-18
Thankyou, I will do.

Meanwhile, here is the output of xrandr:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0

---

### Post by WasMeHere on 2011-10-18
> **tommy2k10 said:**
> 
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   ...
Hello again tommy2k10,

You have only low resolution. Unless you have a very old monitor, an nvidia card with a proprietary nvidia driver should not behave like this.

1. Did you download it from the nvidia web site or are you using the proprietary nvidia driver offered via the built-in Ubuntu program via the menu? (Both should work, and the built-in method is much simpler)
*System -- Administration -- Proprietary Hardware Drivers*
Actually the program name is 
```
/usr/bin/jockey-gtk
```

I looked closer at the card specs: product: C61 [GeForce 6150SE nForce 430]. This is not what I thought at first (GT 430) but a much older card (from 2005) according to the following wiki page
[[COLOR="RoyalBlue"]_http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_Go_6_.28Go_6xxx.29_series_[/COLOR]]("http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#GeForce_Go_6_.28Go_6xxx.29_series").

2. Did you double-check at the nvidia web-site that your card is supported by the driver you downloaded?

> Version: 285.05.09 Certified
Release Date: 2011.10.05
Operating System: Linux
Language: English (U.S.)
File Size: 32 MB

3. Run the following command and post its output
```
glxinfo|grep -i opengl
```
You should have a line similar to 
```
OpenGL version string: 2.1.2 NVIDIA 195.36.24
```
which contains the version number of your driver (It is probably *not 195.36.24*, what is it?)

---

### Post by tommy2k10 on 2011-10-19
1) I got it from the proprietary drivers.
2) It is supported

3) This is the output from gxlgrep:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 280.13
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:

---

### Post by WasMeHere on 2011-10-19
> **tommy2k10 said:**
> 1) I got it from the proprietary drivers.
2) It is supported

3) This is the output from gxlgrep:

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.2 NVIDIA 280.13
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
OpenGL extensions:
Another computer at my house has Ubuntu Studio 11.04 the following nvidia driver was installed via the built-in system:
**version 270.41.06**. It works well including the highest resolution of the monitor (1920x1080).
This is slightly older than the one you are running, and I suspect that your problem is related to the new software versions introduced in Ubuntu 11.10. 

Now let us go backwards for a while:

- Did you upgrade your Ubuntu to 11.10, or was this your first Ubuntu installation?

- Can you run your computer with another operating system or version and get good graphics (for example Windows XP, Ubuntu 10.04, Knoppix, Linux Mint 9 ...)? Remember that you can run most linux versions *live* from the installation media (CD or USB drive)! What system works? This is to find out if there is something wrong with your hardware. 

- Would it be a possible alternative for you to install the stable Ubuntu 10.04 'lucid lynx' LTS (Long Time Support) version? It would certainly support your video card, but I don't know if you have some other application or hardware unit that would need a brand new operating system.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by nervis on 2011-10-19
I have a similar problem.I cant install nvidia driver since ubuntu 9.10,when I install it I cant entry in graphic mode,only in recovery mode but in ubuntu 11.10 I havent the option "run ubuntu in low-graphics mode for just one session".


I install graphics drivers from synaptics,from terminal,install .RUN script,from jockey but I have the same problem.my card is Nvidia geforce 9600gt

sorry my horrible english

---

### Post by WasMeHere on 2011-10-20
> **nervis said:**
> I have a similar problem.I cant install nvidia driver since ubuntu 9.10,when I install it I cant entry in graphic mode,only in recovery mode but in ubuntu 11.10 I havent the option "run ubuntu in low-graphics mode for just one session".


I install graphics drivers from synaptics,from terminal,install .RUN script,from jockey but I have the same problem.my card is Nvidia geforce 9600gt

sorry my horrible english

Hi nervis,

Your card is fairly modern, it was introduced to the market in 2008 (according to a wiki list). According to nvidia's own site, the same driver is recommended as for *tommy2k10*'s card). These problems do not make sense to me. What operating system are you running now and on what hardware? How is your standard Ubuntu graphics driver working (*not* nvidia)?

[COLOR="Red"]Let us call for help from someone with lots of experience with nvidia cards and drivers![/COLOR]

Looking forward to a helping hand
Olle

---

### Post by nervis on 2011-10-20
> **Olle Wiklund said:**
> Hi nervis,

Your card is fairly modern, it was introduced to the market in 2008 (according to a wiki list). According to nvidia's own site, the same driver is recommended as for *tommy2k10*'s card). These problems do not make sense to me. What operating system are you running now and on what hardware? How is your standard Ubuntu graphics driver working (*not* nvidia)?

[COLOR=Red]Let us call for help from someone with lots of experience with nvidia cards and drivers![/COLOR]

Looking forward to a helping hand
Olle

thanks olle.I have ubuntu 11.10

This is my hardware:

PCI (sysfs)  
H/W path            Device      Class       Description
=======================================================
                                system      Desktop Computer
/0                              bus         MS-7255
/0/0                            memory      128KiB BIOS
/0/4                            processor   Intel(R) Core(TM)2 CPU          6420
/0/4/8                          memory      32KiB L1 cache
/0/4/0.1                        processor   Logical CPU
/0/4/0.2                        processor   Logical CPU
/0/19                           memory      2GiB System Memory
/0/19/0                         memory      1GiB DIMM
/0/19/1                         memory      1GiB DIMM
/0/2                            processor   
/0/2/0.1                        processor   Logical CPU
/0/2/0.2                        processor   Logical CPU
/0/100                          bridge      P4M890 Host Bridge
/0/100/0.5                      generic     P4M890 I/O APIC Interrupt Controller
/0/100/1                        bridge      VT8237/VX700 PCI Bridge
/0/100/2                        bridge      P4M890 PCI to PCI Bridge Controller
/0/100/2/0                      display     G94 [GeForce 9600 GT]
/0/100/3                        bridge      P4M890 PCI to PCI Bridge Controller
/0/100/9            eth1        network     RTL-8169 Gigabit Ethernet
/0/100/f            scsi0       storage     VT8237A SATA 2-Port Controller
/0/100/f/0.0.0      /dev/sda    disk        500GB ST3500830AS
/0/100/f/0.0.0/1    /dev/sda1   volume      323GiB Windows NTFS volume
/0/100/f/0.0.0/2    /dev/sda2   volume      29GiB EXT4 volume
/0/100/f/0.0.0/3    /dev/sda3   volume      112GiB Extended partition
/0/100/f/0.0.0/3/5  /dev/sda5   volume      4000MiB Linux swap / Solaris partiti
/0/100/f/0.0.0/3/6  /dev/sda6   volume      108GiB Linux filesystem partition
/0/100/f.1          scsi2       storage     VT82C586A/B/VT82C686/A/B/VT823x/A/C 
/0/100/f.1/0.0.0    /dev/cdrom  disk        DVDRAM GSA-H42N
/0/100/10                       bus         VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                     bus         VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                     bus         VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                     bus         VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                     bus         USB 2.0
/0/100/11                       bridge      VT8237A PCI to ISA Bridge
/0/100/12           eth0        network     VT6102 [Rhine-II]
/0/101                          bridge      P4M890 Host Bridge
/0/102                          bridge      P4M890 Host Bridge
/0/103                          bridge      P4M890 Host Bridge
/0/104                          bridge      P4M890 Host Bridge
/0/105                          bridge      P4M890 Security Device
/0/106                          bridge      P4M890 Host Bridge
/0/107                          bridge      VT8237/8251 Ultra VLINK Controller
/0/108                          bridge      VT8237A Host Bridge
/0/1                            multimedia  VT8237A/VT8251 HDA Controller
/0/3                scsi4       storage     
/0/3/0.0.0          /dev/sdb    disk        Flash HS-CF
/0/3/0.0.0/0        /dev/sdb    disk        
/0/3/0.0.1          /dev/sdc    disk        Flash HS-MS/SD
/0/3/0.0.1/0        /dev/sdc    disk        
/0/3/0.0.2          /dev/sdd    disk        Flash HS-SM
/0/3/0.0.2/0        /dev/sdd    disk        

point of view 9600 gt


I run in ubuntu witout graphics drivers,when I install drivers ubuntu no works

---

### Post by tommy2k10 on 2011-10-20
1) I upgraded from Ubuntu 11.04 to 11.10, but I did a clean install (I had 11.04 before!, which was fine.

2) Windows XP, Vista and 7 are fine with the graphics card.

---

### Post by WasMeHere on 2011-10-20
> **tommy2k10 said:**
> 1) I upgraded from Ubuntu 11.04 to 11.10, but I did a clean install (I had 11.04 before!, which was fine.

2) Windows XP, Vista and 7 are fine with the graphics card.

I suggest that you return to Ubuntu 11.04 and run it for some time (a few weeks). Test 11.10 live from a CD/USB drive (and 'install' the nvidia driver into the live system)! When that works you should be able to install 11.10 to your hard drive again.

---

### Post by WasMeHere on 2011-10-20
> **nervis said:**
> thanks olle.I have ubuntu 11.10

This is my hardware:

PCI (sysfs)  
H/W path            Device      Class       Description
=======================================================
                                system      Desktop Computer
/0                              bus         MS-7255
/0/0                            memory      128KiB BIOS
/0/4                            processor   Intel(R) Core(TM)2 CPU          6420
/0/4/8                          memory      32KiB L1 cache
/0/4/0.1                        processor   Logical CPU
/0/4/0.2                        processor   Logical CPU
/0/19                           memory      2GiB System Memory
/0/19/0                         memory      1GiB DIMM
/0/19/1                         memory      1GiB DIMM
...
/0/100/2                        bridge      P4M890 PCI to PCI Bridge Controller
/0/100/2/0                      display     G94 [GeForce 9600 GT]
---
point of view 9600 gt

I run in ubuntu witout graphics drivers,when I install drivers ubuntu no works

Does your card work well with Windows? What other Ubuntu versions (between 9.10 and 11.10) have you tried? Do you still have an installation disk for 9.10? In that case run Ubuntu ***live*** from it to verify that it works. Also, I also suggest that you download a current version of the long time support version Ubuntu 10.04 lucid lynx LTS. I think you have a fair chance that the graphics work now, even if it did not work when 10.04 was released. Run it ***live*** and try to 'install into the live system' the nvidia graphics driver offered by the system!

---

### Post by nervis on 2011-10-20
> **Olle Wiklund said:**
> Does your card work well with Windows? What other Ubuntu versions (between 9.10 and 11.10) have you tried? Do you still have an installation disk for 9.10? In that case run Ubuntu ***live*** from it to verify that it works. Also, I also suggest that you download a current version of the long time support version Ubuntu 10.04 lucid lynx LTS. I think you have a fair chance that the graphics work now, even if it did not work when 10.04 was released. Run it ***live*** and try to 'install into the live system' the nvidia graphics driver offered by the system!

yes,my card work well with windows.I tested with ubuntu 10.04,10.10,11.04 and 11.10.

I have it errors in Xorg.0.log

(WW)the directory /usr/share/fonts/X11/cyrilic does no exit
(WW)the directory /usr/share/fonts/X11/100dpi
(WW)the directory /usr/share/fonts/75dpi
(WW)hotplugging is on,devices using drivers"kbd" mouse or "vmmouse" will de disabled
(WW)disabling keyboard0
(WW)disabling mouse0

it happens with the last nvidia.run

---

### Post by WasMeHere on 2011-10-21
> **nervis said:**
> yes,my card work well with windows.I tested with ubuntu 10.04,10.10,11.04 and 11.10.

I have it errors in Xorg.0.log

(WW)the directory /usr/share/fonts/X11/cyrilic does no exit
(WW)the directory /usr/share/fonts/X11/100dpi
(WW)the directory /usr/share/fonts/75dpi
(WW)hotplugging is on,devices using drivers"kbd" mouse or "vmmouse" will de disabled
(WW)disabling keyboard0
(WW)disabling mouse0

it happens with the last nvidia.run
0. From the Windows experience: your card is OK. From the error log: Do you use the cyrillic letters? Maybe there was some error when upgrading from 9.10, so that some directory and font files are missing. Or maybe the nvidia driver does not support cyrillic letters?

1. Do you still run Ubuntu 9.10?

2. How does your graphics work, when you run Ubuntu live from an installation media (CD or USB drive)? Do you get the desired resolution? Do you get the desired locale (language, keyboard: letters, fonts ...)?

3. When you tested with > ubuntu 10.04,10.10,11.04 and 11.10 what did you test?

- Did you try to upgrade from your existing version?
- Did you run live sessions (with default graphics, or with a proprietary driver, what language, what keyboard)?
- Did you try to install Ubuntu from a live session?
Where and how did your problems start?

---

### Post by nervis on 2011-10-21
> **Olle Wiklund said:**
> 0. From the Windows experience: your card is OK. From the error log: Do you use the cyrillic letters? Maybe there was some error when upgrading from 9.10, so that some directory and font files are missing. Or maybe the nvidia driver does not support cyrillic letters?

1. Do you still run Ubuntu 9.10?

2. How does your graphics work, when you run Ubuntu live from an installation media (CD or USB drive)? Do you get the desired resolution? Do you get the desired locale (language, keyboard: letters, fonts ...)?

3. When you tested with  what did you test?

- Did you try to upgrade from your existing version?
- Did you run live sessions (with default graphics, or with a proprietary driver, what language, what keyboard)?
- Did you try to install Ubuntu from a live session?
Where and how did your problems start?

0.I dont use ciliryc letters.I am using letters in default in ubuntu 11.10.I never update ubuntu to other version,I always  format my hard disk.
1.no
2.the last version that runing  graphics drivers was 9.10,resolution 1280x1024,(max resolution for my monitor)and spanish keyboard and lenguage was correct.installed from cd 
3.my problems start when I install ubuntu 10.04

I hope you understand my basic english.sorry

---

### Post by WasMeHere on 2011-10-22
> **nervis said:**
> 0.I dont use ciliryc letters.I am using letters in default in ubuntu 11.10.I never update ubuntu to other version,I always  format my hard disk.
1.no
2.the last version that runing  graphics drivers was 9.10,resolution 1280x1024,(max resolution for my monitor)and spanish keyboard and lenguage was correct.installed from cd 
3.my problems start when I install ubuntu 10.04

I hope you understand my basic english.sorry
English is a foreign language to me too, and I think we can manage the language. The problem for me is to understand how your computer is behaving, because it is different from mine, and *[COLOR="Red"]maybe there is something that you think is not important, that would make me or someone else reading this thread understand[/COLOR]*.

Anyway we won't worry about the lack of cyrillic fonts. And you have no problem with updating because you install fresh versions of Ubuntu. But you cannot use any nvidia driver beginning with 10.04.

What flavour of Ubuntu are you running now? Are you running *Ubuntu server*, 'vanilla' Ubuntu with unity or gnome, Kubuntu, Xubuntu, Lubuntu, Ubuntu Studio, Mythbuntu or some Alternate version? Are you running it in text mode now, or do you have graphics with the default graphics driver? What resolution?

I hope you can be patient and let me ask again about live sessions:

2. How does your graphics work, when you run Ubuntu live from an installation media (CD or USB drive)? Do you get the desired resolution? Do you get the desired locale (language, keyboard: letters, fonts ...)? If your installation media does not provide a live session (only installation), maybe you can download the iso file of a version with live session (for example 'vanilla' Ubuntu, Kubuntu, Xubuntu).

3. When you tested, what did you test and where and how did your problems start (during the testing in the live session)?

---

### Post by nervis on 2011-10-22
> **Olle Wiklund said:**
> English is a foreign language to me too, and I think we can manage the language. The problem for me is to understand how your computer is behaving, because it is different from mine, and *[COLOR=Red]maybe there is something that you think is not important, that would make me or someone else reading this thread understand[/COLOR]*.

Anyway we won't worry about the lack of cyrillic fonts. And you have no problem with updating because you install fresh versions of Ubuntu. But you cannot use any nvidia driver beginning with 10.04.

What flavour of Ubuntu are you running now? Are you running *Ubuntu server*, 'vanilla' Ubuntu with unity or gnome, Kubuntu, Xubuntu, Lubuntu, Ubuntu Studio, Mythbuntu or some Alternate version? Are you running it in text mode now, or do you have graphics with the default graphics driver? What resolution?

I hope you can be patient and let me ask again about live sessions:

2. How does your graphics work, when you run Ubuntu live from an installation media (CD or USB drive)? Do you get the desired resolution? Do you get the desired locale (language, keyboard: letters, fonts ...)? If your installation media does not provide a live session (only installation), maybe you can download the iso file of a version with live session (for example 'vanilla' Ubuntu, Kubuntu, Xubuntu).

3. When you tested, what did you test and where and how did your problems start (during the testing in the live session)?

I am using ubuntu 11.10 desktop 32 bits,(I test with 64 bits version but the same problem)
no xubuntu,mythubuntu o others versions,only ubuntu.with nouveau drivers I can start my ubuntu but I alwais unistall it and install nvidia drivers beacuse nouveau no have 3d.

---

### Post by WasMeHere on 2011-10-22
> **nervis said:**
> I am using ubuntu 11.10 desktop 32 bits,(I test with 64 bits version but the same problem)
no xubuntu,mythubuntu o others versions,only ubuntu.with nouveau drivers I can start my ubuntu but I alwais unistall it and install nvidia drivers beacuse nouveau no have 3d.

So it works well with 2D with 'all' drivers, and it works with the driver downloaded from nvidia's web site with 3D. Now I don't understand. What is the problem in 3D? Or is the problem, that you cannot obtain 3D?

*Edit: I am sorry for not understanding and asking questions that were not relevant, nervis. Now I think that Ubuntu works well in your computer with the driver downloaded from nvidia's web site. I assumed that you needed help with something, Sorry for that :-( *

---

### Post by tommy2k10 on 2011-10-24
I've just noticed this:

When I go to System Settings - Additional Drivers, it says 'Proprietary drivers are being used to make this system work properly.'

Sorry for not spotting this earlier.

---

### Post by WasMeHere on 2011-10-24
Hi Tommy,

Was it a temporary problem (because 11.10 was so new)? Is Ubuntu working well with your computer now, or do you need help with something?

Have fun finding out :-)
Olle

---

### Post by tommy2k10 on 2011-10-24
The graphics are still not as they should be, but I'll cope!!
I have got a completely unrelated problem, but that's for another section I think!

---

### Post by WasMeHere on 2011-10-24
> **ps8437 said:**
> I have been having problems with my [GeForce 8400 GS]("http://ubuntuforum.webs.com/home.htm"). I have installed the proprietary drivers however it says they are not in use. The only real issue I am having is overscan but everything else works fine. I have [followed]("http://ubuntuforum.webs.com/home.htm") some of these [steps]("http://ubuntuforum.webs.com/home.htm").
Hello ps8437,

Is your problems related to the new version 11.10? Have you tried earlier versions? And what flavour of Ubuntu are you using ('vanilla', kubuntu, xubuntu, lubuntu ...)? There is one choice to ***install*** the 'accelerated nvidia driver' and another choice to ***activate*** it in the GUI of

*jockey-gtk* alias

*System -- Administration -- Proprietary Hardware Drivers* (or something meaning the same depending on language).

So, yes, it can be installed but not activated, and it should be easy to activate or deactivate in that window (of jockey-gtk).

What happens when you activate it and reboot the computer?

Have fun finding out :-)
Olle

---

### Post by nervis on 2011-10-25
> **Olle Wiklund said:**
> So it works well with 2D with 'all' drivers, and it works with the driver downloaded from nvidia's web site with 3D. Now I don't understand. What is the problem in 3D? Or is the problem, that you cannot obtain 3D?

*Edit: I am sorry for not understanding and asking questions that were not relevant, nervis. Now I think that Ubuntu works well in your computer with the driver downloaded from nvidia's web site. I assumed that you needed help with something, Sorry for that :-( *

no olle,don,t work.today test with nvidia drivers 96 and I can see in my xorg.conf resolution(1280x1024) but no work.whit the others drivers I can´t see resolution in my xorg.conf.

---

### Post by WasMeHere on 2011-10-25
> **nervis said:**
> no olle,don,t work.today test with nvidia drivers 96 and I can see in my xorg.conf resolution(1280x1024) but no work.whit the others drivers I can´t see resolution in my xorg.conf.
Hello again nervis,

You wrote earlier that you install nvidia drivers because 'nouveau no have 3d'. Does it mean that the nouveau drivers work well in 2D? If that is the case I suggest that you run with 2D for some weeks and try again, when several bugs have been found and fixed in 11.10. Otherwise I suggest installing an older version of Ubuntu, for example 10.04 LTS or 11.04.

Trying to help
Olle

---

### Post by nervis on 2011-10-26
> **Olle Wiklund said:**
> Hello again nervis,

You wrote earlier that you install nvidia drivers because 'nouveau no have 3d'. Does it mean that the nouveau drivers work well in 2D? If that is the case I suggest that you run with 2D for some weeks and try again, when several bugs have been found and fixed in 11.10. Otherwise I suggest installing an older version of Ubuntu, for example 10.04 LTS or 11.04.

Trying to help
Olle

but I have the same problem with others versions,nouveau run well with 2d but I wan run whith nvidia drivers but it is imposible.maybe install 11.04 because I can have "run ubuntu in low-graphics mode for just one session" in 11.10 I can´t see it option.thanks olle for you patience

---

### Post by nervis on 2011-10-26
this is my Xorg.0.log with nvidia 96 drivers:

```
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    20.477] X Protocol Version 11, Revision 0
[    20.477] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    20.477] Current Operating System: Linux nervis-MS-7255 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    20.477] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=b09487c0-7c9b-496e-8cdd-6e669089ec30 ro quiet splash vt.handoff=7
[    20.477] Build Date: 13 October 2011  05:33:17PM
[    20.477] xorg-server 2:1.10.4-1ubuntu4.1 (For technical support please see http://www.ubuntu.com/support) 
[    20.477] Current version of pixman: 0.22.2
[    20.477]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.477] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.477] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 25 14:40:50 2011
[    20.477] (==) Using config file: "/etc/X11/xorg.conf"
[    20.477] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.673] (==) ServerLayout "Layout0"
[    20.673] (**) |-->Screen "Screen0" (0)
[    20.673] (**) |   |-->Monitor "Monitor0"
[    20.673] (**) |   |-->Device "Device0"
[    20.673] (**) |-->Input Device "Keyboard0"
[    20.673] (**) |-->Input Device "Mouse0"
[    20.674] (==) Automatically adding devices
[    20.674] (==) Automatically enabling devices
[    20.674] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.674]     Entry deleted from font path.
[    20.674] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.674]     Entry deleted from font path.
[    20.674] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.674]     Entry deleted from font path.
[    20.674] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.674]     Entry deleted from font path.
[    20.674] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    20.674] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.674] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    20.674] (WW) Disabling Keyboard0
[    20.674] (WW) Disabling Mouse0
[    20.674] (II) Loader magic: 0x823ada0
[    20.674] (II) Module ABI versions:
[    20.674]     X.Org ANSI C Emulation: 0.4
[    20.674]     X.Org Video Driver: 10.0
[    20.674]     X.Org XInput driver : 12.3
[    20.674]     X.Org Server Extension : 5.0
[    20.675] (--) PCI:*(0:2:0:0) 10de:0622:1acc:0961 rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/524288
[    20.675] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.675] (II) LoadModule: "extmod"
[    20.716] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    20.716] (II) Module extmod: vendor="X.Org Foundation"
[    20.716]     compiled for 1.10.4, module version = 1.0.0
[    20.716]     Module class: X.Org Server Extension
[    20.716]     ABI class: X.Org Server Extension, version 5.0
[    20.716] (II) Loading extension MIT-SCREEN-SAVER
[    20.716] (II) Loading extension XFree86-VidModeExtension
[    20.716] (II) Loading extension XFree86-DGA
[    20.716] (II) Loading extension DPMS
[    20.716] (II) Loading extension XVideo
[    20.716] (II) Loading extension XVideo-MotionCompensation
[    20.716] (II) Loading extension X-Resource
[    20.716] (II) LoadModule: "dbe"
[    20.717] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    20.717] (II) Module dbe: vendor="X.Org Foundation"
[    20.717]     compiled for 1.10.4, module version = 1.0.0
[    20.717]     Module class: X.Org Server Extension
[    20.717]     ABI class: X.Org Server Extension, version 5.0
[    20.717] (II) Loading extension DOUBLE-BUFFER
[    20.717] (II) LoadModule: "glx"
[    20.717] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    21.316] (II) Module glx: vendor="NVIDIA Corporation"
[    21.326]     compiled for 4.0.2, module version = 1.0.0
[    21.326]     Module class: X.Org Server Extension
[    21.326] (II) NVIDIA GLX Module  96.43.20  Sun Jul 17 23:48:16 PDT 2011
[    21.326] (II) Loading extension GLX
[    21.326] (II) LoadModule: "record"
[    21.327] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.328] (II) Module record: vendor="X.Org Foundation"
[    21.328]     compiled for 1.10.4, module version = 1.13.0
[    21.328]     Module class: X.Org Server Extension
[    21.328]     ABI class: X.Org Server Extension, version 5.0
[    21.328] (II) Loading extension RECORD
[    21.328] (II) LoadModule: "dri"
[    21.329] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.329] (II) Module dri: vendor="X.Org Foundation"
[    21.329]     compiled for 1.10.4, module version = 1.0.0
[    21.329]     ABI class: X.Org Server Extension, version 5.0
[    21.329] (II) Loading extension XFree86-DRI
[    21.329] (II) LoadModule: "dri2"
[    21.329] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.330] (II) Module dri2: vendor="X.Org Foundation"
[    21.330]     compiled for 1.10.4, module version = 1.2.0
[    21.330]     ABI class: X.Org Server Extension, version 5.0
[    21.330] (II) Loading extension DRI2
[    21.330] (II) LoadModule: "nvidia"
[    21.330] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.430] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.430]     compiled for 4.0.2, module version = 1.0.0
[    21.430]     Module class: X.Org Video Driver
[    21.459] (II) NVIDIA dlloader X Driver  96.43.20  Sun Jul 17 23:35:47 PDT 2011
[    21.469] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.469] (++) using VT number 7

[    21.470] (II) Loading sub module "fb"
[    21.470] (II) LoadModule: "fb"
[    21.470] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.470] (II) Module fb: vendor="X.Org Foundation"
[    21.470]     compiled for 1.10.4, module version = 1.0.0
[    21.470]     ABI class: X.Org ANSI C Emulation, version 0.4
[    21.470] (II) Loading sub module "ramdac"
[    21.470] (II) LoadModule: "ramdac"
[    21.470] (II) Module "ramdac" already built-in
[    21.482] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.482] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.483] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.483] (==) NVIDIA(0): RGB weight 888
[    21.483] (==) NVIDIA(0): Default visual is TrueColor
[    21.483] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.484] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.484] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.484] (II) NVIDIA(0):     enabled.
[    21.490] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:2:0:0. 
[    21.490] (EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
[    21.490] (EE) NVIDIA(0):     additional information.
[    21.490] (EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
[    21.490] (EE) NVIDIA(0):  *** Aborting ***
[    21.490] (II) UnloadModule: "nvidia"
[    21.490] (II) Unloading nvidia
[    21.490] (II) UnloadModule: "fb"
[    21.490] (II) Unloading fb
[    21.490] (EE) Screen(s) found, but none have a usable configuration.
[    21.490] 
Fatal server error:
[    21.490] no screens found
[    21.490] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    21.490] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    21.490] 
[    21.496]  ddxSigGiveUp: Closing log

```

---

### Post by WasMeHere on 2011-10-26
Sometimes you have to try several linux versions and flavours until you find something that cooperates well with your computer hardware.

Consider downloading the iso file of Xubuntu 11.04 and Linux Mint 11. Make live CD or USB drives and run the systems live without installing, just to see if they works better than 'vanilla' Ubuntu. If it looks promising, I suggest that you backup your personal files and install that system instead.

---

### Post by Hammadnadeemx on 2011-10-27
i am new to linux and i also have a problem with nvidia drivers. i have managed to remove novea and installed nvidia 285 linux drivers latest using the update command . I see the nvidia xserver server settings and when i click it it shows that the up to date driver is install but THE system info tool says graphics unknown , opengl render unknown, driver unknown , experience fall back . and last but not least x server does not seem to be saving any settings as i ticked texture sharpening but after reboot it was UN ticked . i have also install gnome  as i do not like that unity crap !  any help appreciated . my system specs are
p4 3.0 ghz
2 gib ram
d915gav
gt 240 512 mb
80 gighdd
dvd rw
 thanks
Ubuntu 11.10 32bit

---

### Post by WasMeHere on 2011-10-27
Welcome to the Ubuntu Forums, *Hammadnadeemx*,

I would repeat the advice in a previous post to you, particularly because you are new to linux.

> **Olle Wiklund said:**
> Sometimes you have to try several linux versions and flavours until you find something that cooperates well with your computer hardware.

Consider downloading the iso file of Xubuntu 11.04 and Linux Mint 11. Make live CD or USB drives and run the systems live without installing, just to see if they works better than 'vanilla' Ubuntu. If it looks promising, I suggest that you backup your personal files and install that system instead.

Have fun, not frustration with linux :-)
Olle

---

### Post by Hammadnadeemx on 2011-10-27
yes but before i asked for help on this forum i search every question on google and the drivers i installed are from the restricted hardware option but still ubuntu says unknown graphics in the system info tool ! everything works fine even the moniter runs at native resolution ( it is also called unknown but xserver calls it l365 which is right ) . the only thing bothering me is the unknown stuff. how can i perform a clean install like they had in windows ? or maybe ubuntu just needs time to mature a llittle . By the way is it possible to update the kernel ? what advantages and disadvantages does it have ? does ubuntu support inf chip set drivers and icc profiles for monitors ?

---

### Post by WasMeHere on 2011-10-28
> **Hammadnadeemx said:**
> ...the only thing bothering me is the unknown stuff. how can i perform a clean install like they had in windows ? or maybe ubuntu just needs time to mature a llittle  Yes, that's what 11.10 needs. But do you need 11.10 right now, or would it be better for you to run an older version?
> **Hammadnadeemx said:**
>  By the way is it possible to update the kernel ? what advantages and disadvantages does it have ? does ubuntu support inf chip set drivers and icc profiles for monitors ?
I don't know enough about these questions.

***Looking forward to someone else to answer***
Olle

---

### Post by nervis on 2011-10-28
Hi olle

today I update the last nvidia drivers on windows 7 and I have the same problem,I cant start windows.windows logo on display and no start.I entry in safe mode and remove the 
last drivers and install olds drivers and perfect.after I install my old nvidia 7500LE on ubuntu 11.10 and it work very fine but only with unity 2d,if entry in unity 3d my desktop is frozen,I can not do anythingwith with my mouse(no responds icons of unity)but ubuntu say my card is compatible with unity 3d:

nervis@nervis-MS-7255:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7500 LE/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.30

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes


regard olle

---

### Post by WasMeHere on 2011-10-29
This is interesting, nervis,

Your experience indicates that the problems are not only because of the new version of Ubuntu (11.10), but also because of a new version of the driver from nvidia. I suggest that you run in 2D until another new driver is released from nvidia. Then try that one and hope 3D will work!

Have fun
Olle

---

### Post by nervis on 2011-10-29
> **Olle Wiklund said:**
> This is interesting, nervis,

Your experience indicates that the problems are not only because of the new version of Ubuntu (11.10), but also because of a new version of the driver from nvidia. I suggest that you run in 2D until another new driver is released from nvidia. Then try that one and hope 3D will work!

Have fun
Olle

new drivers 290.03 beta is out.I will test this afternoon

thanks from spain

---

### Post by tommy2k10 on 2011-12-19
The graphics is still not right!
I notice that there is a new NVIDIA (Nov 2011) driver for Linux, I downloaded it, and tried to  install it, but everytime it asks me to stop the X server.
However, whatever method I use:

sudo lightdm
CTRL+ALT+F1

and even

init

I get Monitor out of range!

---

### Post by WasMeHere on 2011-12-19
From a text terminal 'ctrl + alt + F1', can you stop the X server? (Find the process and kill it) and then run the install script.

---

### Post by tommy2k10 on 2011-12-20
No, I get the monitor out of range message and I can only power off the machine!  No key combinations work after that!

---

### Post by WasMeHere on 2011-12-20
In the header you have Lubuntu. In your first post you wrote that you run ubuntu 11.10.

What version and flavour are you running now? Is it installed to the hard drive or persistent live?

Assuming it is Lubuntu 11.10 and installed. Can you select recovery mode at the grub menu? And go on from there ...

---

### Post by tommy2k10 on 2011-12-21
No, it is Ubuntu 11.10!

---

### Post by WasMeHere on 2011-12-21
Installed, OK? Can you select recovery mode at the grub menu? And go on from there ... I'm only guessing, I have tried and must admit that I failed to turn off the graphics, so I could not install it either.

The best way to attract readers that might be able to help you (people who have done it already), is probably to ***start a new thread*** with an appropriate title, something like 'install proprietary driver downloaded from nvidia' and post it in the subforum 'Hardware & Laptops'. And write a fairly short but relevant description about the computer, graphics card, Ubuntu version, your problem and what you want to do.

But of course, let us hope someone who reads the end of this thread can help you.

By the way, is it an option for you to run an older version of Ubuntu?

Anyway, good luck :-)
Olle

---

### Post by tommy2k10 on 2011-12-21
I don't have a GRUB menu come up, Ubuntu 11.10 is my only OS on here.  I could install an older version and have them side by side.

---

### Post by WasMeHere on 2011-12-21
> **tommy2k10 said:**
> I don't have a GRUB menu come up, Ubuntu 11.10 is my only OS on here.  I could install an older version and have them side by side.

Or directly: "You may have to hold the SHIFT button on your keyboard while booting up to get this menu to show. If only one operating system is installed on your computer, it may load it automatically without displaying this menu." according to
[[COLOR="RoyalBlue"]_http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/_[/COLOR]]("http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/")

---

### Post by tommy2k10 on 2011-12-21
After editing grub to try and stop the X server (unsuccessfully) and updating GRUB, I installed Startup Manager, changed the resolution to 1024 x 768 (for some odd reason Ubuntu was 800x600 in Hardware Devices) and now I've got a GRUB menu too, with a choice of booting to Win XP, or two one of two copies of Ubuntu! 
The only slight niggle is the desktop looks the same as before, but I don't get any Out of Range messages anymore!

---

### Post by WasMeHere on 2011-12-21
I don't understand. What graphics are you getting now? Can you run Ubuntu and get decent graphics? Or is it only looking better during the boot? Are you trying various boot options?

What about making a new thread to attract new people to help?

---

### Post by tommy2k10 on 2011-12-22
I am getting 1024 x 768, but it doesn't look that different!  I'm not getting the Input signal Out Of Range error message.  I am now getting a GRUB menu instead!  
I've posted in the Hardware forum.

---

### Post by WasMeHere on 2011-12-22
> **tommy2k10 said:**
> I am getting 1024 x 768, but it doesn't look that different!  I'm not getting the Input signal Out Of Range error message.  I am now getting a GRUB menu instead!  
I've posted in the Hardware forum.
OK, I'll subscribe to the thread, but I won't write in it now, I'll wait for others to 'take the command', hoping for some people with the relevant experience to solve your problem.

And I'll be busy with relatives and friends for one week during the holiday season.

Have a nice holiday season and good luck :-)
Olle

---

### Post by tommy2k10 on 2011-12-23
Same here mate -  have a great Christmas and New Year!

---

