---
title: "Can't install Nvidia driver."
date: 2010-04-13
forum: General Help
---

### Post by GibsonSGKing on 2010-04-13
I've tried linux many times in the past, and I'm always irritated to the point of formatting it, shredding the disk, and cursing it while enjoying my windows. Anyhow, (for some reason beyond me) I'm trying it again. Let me start off with the fact that I am very very irritated with how difficult this is becoming (why the hell can't nvidia just make a driver I can install without all of this crap?). OK, so I know how to cd to a directory, login as root. Any time I try to install the nvidia driver, it tells me I need to close X. I've tried going into the recovery terminal and it tells me this. I've also tried the command "/etc/init.d/gdm stop" and then it just takes me to a black screen. I can't do anything from there but push ctrl+alt+delete to restart. So, if anyone can give me simple steps that would be great. I don't want to learn how to use the OS, I just want to install this driver so I can read text and more than half of my monitor is displayed on, then I'll worry about learning. Thank you for your time.


Oh, also, I'm on linux hardy heron 8.04

---

### Post by DeMus on 2010-04-13
> **GibsonSGKing said:**
> I've tried linux many times in the past, and I'm always irritated to the point of formatting it, shredding the disk, and cursing it while enjoying my windows. Anyhow, (for some reason beyond me) I'm trying it again. Let me start off with the fact that I am very very irritated with how difficult this is becoming (why the hell can't nvidia just make a driver I can install without all of this crap?). OK, so I know how to cd to a directory, login as root. Any time I try to install the nvidia driver, it tells me I need to close X. I've tried going into the recovery terminal and it tells me this. I've also tried the command "/etc/init.d/gdm stop" and then it just takes me to a black screen. I can't do anything from there but push ctrl+alt+delete to restart. So, if anyone can give me simple steps that would be great. I don't want to learn how to use the OS, I just want to install this driver so I can read text and more than half of my monitor is displayed on, then I'll worry about learning. Thank you for your time.


Oh, also, I'm on linux hardy heron 8.04

I installed the driver, on Jaunty btw, using a PPA. Just do this:

Visit [nVidia PPA page]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") and click on the green text saying [COLOR="Lime"]Technical details about this PPA[/COLOR].
It unfolds the instructions what to do next.
Add the two lines to the sources.list file using Synaptics.
Add the matching signing key as well, reload the contents in Synaptic and look for nVidia.
You will be presented with the latest driver available for your OS.
Install it.
Reboot.
Open menu System - Administration - Hardware drivers and activate the driver.
Reboot again and you are done.
Success.

---

### Post by GibsonSGKing on 2010-04-13
> **DeMus said:**
> I installed the driver, on Jaunty btw, using a PPA. Just do this:

Visit [nVidia PPA page]("https://launchpad.net/~nvidia-vdpau/+archive/ppa") and click on the green text saying [COLOR="Lime"]Technical details about this PPA[/COLOR].
It unfolds the instructions what to do next.
Add the two lines to the sources.list file using Synaptics.
Add the matching signing key as well, reload the contents in Synaptic and look for nVidia.
You will be presented with the latest driver available for your OS.
Install it.
Reboot.
Open menu System - Administration - Hardware drivers and activate the driver.
Reboot again and you are done.
Success.
Thank you for the help, but what is Synaptic and how do you use it?

---

### Post by philinux on 2010-04-13
> **GibsonSGKing said:**
> I've tried linux many times in the past, and I'm always irritated to the point of formatting it, shredding the disk, and cursing it while enjoying my windows. Anyhow, (for some reason beyond me) I'm trying it again. Let me start off with the fact that I am very very irritated with how difficult this is becoming (why the hell can't nvidia just make a driver I can install without all of this crap?). OK, so I know how to cd to a directory, login as root. Any time I try to install the nvidia driver, it tells me I need to close X. I've tried going into the recovery terminal and it tells me this. I've also tried the command "/etc/init.d/gdm stop" and then it just takes me to a black screen. I can't do anything from there but push ctrl+alt+delete to restart. So, if anyone can give me simple steps that would be great. I don't want to learn how to use the OS, I just want to install this driver so I can read text and more than half of my monitor is displayed on, then I'll worry about learning. Thank you for your time.


Oh, also, I'm on linux hardy heron 8.04

What do you get offered under system>admin>hardware drivers

---

### Post by GibsonSGKing on 2010-04-13
> **philinux said:**
> What do you get offered under system>admin>hardware drivers

Not a thing. 

My specs are as follows btw:

Intel E5200
EVGA GTS250
2GB DDR2 800
Foxonn G31AX-K


I just noticed I didn't include them :P

---

### Post by TheConsaw on 2010-04-13
why use such an old version of ubuntu, nvidia is pretty well supported in any of the installs ive done on much newer versions,
no head aches, just click hardware drivers and those puppies install themselves automatically !

---

### Post by GibsonSGKing on 2010-04-13
> **TheConsaw said:**
> why use such an old version of ubuntu, nvidia is pretty well supported in any of the installs ive done on much newer versions,
no head aches, just click hardware drivers and those puppies install themselves automatically !

Because I already have this installed? I don't even know how to update linux. I hardly know anything about it. I've dealt with a little bit of server stuff, but hardly anything at all really.

---

### Post by GibsonSGKing on 2010-04-13
Where did everyone go? I take it no one wants to help me?

---

### Post by howefield on 2010-04-13
> **TheConsaw said:**
> why use such an old version of ubuntu,..

It is the current LTS, not the worst choice in the world...

---

### Post by howefield on 2010-04-13
> **GibsonSGKing said:**
> Where did everyone go? I take it no one wants to help me?

DeMus has given you help.

System > Administration > Synaptic Package Manager and click on the Settings > Repositories menu, then Other Software tab...

That's where to add the information to your sources.list as described.

---

### Post by GibsonSGKing on 2010-04-13
> **howefield said:**
> DeMus has given you help.

System > Administration > Synaptic Package Manager and click on the Settings > Repositories menu, then Other Software tab...

That's where to add the information to your sources.list as described.

Thank you. I was just worried I said something wrong or something :-S


Ok, thank you. I'm a total noob with this stuff, so I need even the most basic things explained lol. I looked up how to use Synaptics for linux, but it came up with touchscreen drivers :-/

Thank you all again, I'll see if I can get it working now...

---

### Post by GibsonSGKing on 2010-04-13
I have it right so far I think, but I'm not sure where to put the signing key in at. Help again please?


EDIT: I think I got it, I clicked the key on the page and copied the text on it, and then put that in a file and imported the file. Anyhow, it seems to be downloading now.

---

### Post by howefield on 2010-04-13
> **GibsonSGKing said:**
> I have it right so far I think, but I'm not sure where to put the signing key in at. Help again please?

Same place, only instead of the Other Software tab, use the Authentication tab.

System > Administration > Synaptic Package Manager and click on the Settings > Repositories menu, then Authentication tab...

---

### Post by GibsonSGKing on 2010-04-13
I downloaded it, think I installed it, and it has a green box next to the driver in Synaptic, but yet when I go to hardware drivers nothing shows up. I don't understand :?

---

### Post by GibsonSGKing on 2010-04-13
Please somebody help, I'm so close to getting this it's painful :-(

---

### Post by GibsonSGKing on 2010-04-13
Bump

/cries

---

### Post by cgb on 2010-04-13
It wont show up under hardware drivers.  Sounds like it should be installed.  You should have Nvidia X Server Settings under your Preferences now.

---

### Post by GibsonSGKing on 2010-04-13
> **cgb said:**
> It wont show up under hardware drivers.  Sounds like it should be installed.  You should have Nvidia X Server Settings under your Preferences now.

Nope. I don't understand it. I've tried 2 versions now, and reinstalling it. It's just a no go ](*,)

---

### Post by cgb on 2010-04-13
Well it may be the Nvidia X Server Settings manager might not install from the PPA by itself.  Not sure on that one.  If not you should be able to lookup nvidia-settings in Synaptic to install it.  Other then this why do you think it didn't install?  Are you having problems with video?  You can verify if it is in fact being used by going into terminal and entering the below code.  There will be a section in the displayed info that states client glx vendor string and it should state NVIDIA Corporation.  

```
glxinfo
```

---

### Post by GibsonSGKing on 2010-04-13
> **cgb said:**
> Well it may be the Nvidia X Server Settings manager might not install from the PPA by itself.  Not sure on that one.  If not you should be able to lookup nvidia-settings in Synaptic to install it.  Other then this why do you think it didn't install?  Are you having problems with video?  You can verify if it is in fact being used by going into terminal and entering the below code.  There will be a section in the displayed info that states client glx vendor string and it should state NVIDIA Corporation.  

```
glxinfo
```
Installing the NvidiaXServer Settings now, and when I put that command into the console this is the output-


```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x3a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```
So I have to think that it's not recognizing my video card. Thank you for all of your help so far as well, I appreciate it a lot :)

---

### Post by cgb on 2010-04-13
Have you restarted since you installed the nvidia driver?  If not try restarting since typically you will need to restart the gdm for it to fully be applied.

---

### Post by GibsonSGKing on 2010-04-13
Installed the control panel thing, and it lowered my res and gave me a setup screen on boot. I put in my settings but it didn't apply them. Also, when I open the Nvidia control panel it tells me "you do not appear to be using the NVIDIAX Driver. Please edit your x configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

When I put nvidia-xconfig in to terminal 

```

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


```

is my output. I'm even more stumped now.


EDIT: Yes, I'm restarting after every change just to make sure.

---

### Post by steveneddy on 2010-04-13
First of all, stop bumping after only an hour - most of us are all around the world, so the best answer may only come after a 24 hour wait.

So - there is no little green icon in the upper right hand corner of Gnome that states something about Hardware Drivers?

Is this an add on card in a desktop which has onboard video already?

Just for grins, run

```
lspci
```

in terminal and post the output here please.

---

### Post by GibsonSGKing on 2010-04-13
> **steveneddy said:**
> First of all, stop bumping after only an hour - most of us are all around the world, so the best answer may only come after a 24 hour wait.

So - there is no little green icon in the upper right hand corner of Gnome that states something about Hardware Drivers?

Is this an add on card in a desktop which has onboard video already?

Just for grins, run

```
lspci
```

in terminal and post the output here please.
I'm sorry, it's just that the forums move fast and I'm afraid if I don't keep my thread at the first page or so, it will be forgotten. That's what's happened the other 4 or so times I've tried linux.

Not that I'm seeing. And when I go to Hardware Drivers in the System menu, it says no proprietary drivers are installed.

This is an add on card, I built this computer myself. It's an Nvidia GTS250, basically a rebranded 9800GTX+

Heres my terminal output:
```

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0615 (rev a2)
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
04:05.0 USB Controller: NEC Corporation USB (rev 43)
04:05.1 USB Controller: NEC Corporation USB (rev 43)
04:05.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```

---

### Post by GibsonSGKing on 2010-04-13
Well, I just wiped everything I installed, and installed the drivers again with the settings file, and now I have my res at normal. I still get the message that "you do not appear to be using the NVIDIAX Driver. Please edit your x configuration file (just run `nvidia-xconfig` as root), and restart the X server. " though.

output is 

```

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

when I use the xconfig command. Ideas? Also, the hardware drivers place in the system menu still says I'm using no proprietary drivers. I'm really confussed now, but at least I'm at a decent res lol.

---

### Post by lidex on 2010-04-13
> **GibsonSGKing said:**
> Well, I just wiped everything I installed, and installed the drivers again with the settings file, and now I have my res at normal. I still get the message that "you do not appear to be using the NVIDIAX Driver. Please edit your x configuration file (just run `nvidia-xconfig` as root), and restart the X server. " though.

output is 

```

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: Unable to determine CoreKeyboard; will rely on X server's built-in
         default configuration.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

when I use the xconfig command. Ideas? Also, the hardware drivers place in the system menu still says I'm using no proprietary drivers. I'm really confussed now, but at least I'm at a decent res lol.

I wouldn't worry about that message - it did write the new xorg.conf but you do have to reboot for it to go into effect.

---

### Post by GibsonSGKing on 2010-04-13
> **lidex said:**
> I wouldn't worry about that message - it did write the new xorg.conf but you do have to reboot for it to go into effect.

I read this and rebooted, and it went from my res that I set back to "low graphics mode". What the heck is going on?!? This is really really annoying, I just want it to work ;_;

---

### Post by heavy metal on 2010-04-13
Gibsonking, try to use the "hardware drivers" option, it can look if there's a driver for your Nvidia or you can try ubuntu 9.10 or wait a few days until the release of Lucid Linx, I have read there will be a new driver for Nvidia PC's in Lucid Linx, I think it will be called Noveau driver or something like that...


P.S. Remember, before you use Hardware drivers option you must run update manager and update ubuntu first...

Another thing, if you are interested in still using ubuntu and you are considering buying a new PC buy a motherboard with an Intel video chipset like the G31 or G41 my pc is using the G41 and it works very good, these chipsets have the best support for ubuntu...

---

### Post by cgb on 2010-04-14
Not entirely sure what is going on.  I have read others have gotten this same card working with no problems, so it shouldn't be support for the card.  I typically don't use the PPA (Synaptic) to install the NVIDIA drivers and I'm not sure if that is the problem in this situation.  You could try installing the newest drivers based on the thread linked below.  Best of luck...

[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

---

### Post by GibsonSGKing on 2010-04-14
> **cgb said:**
> Not entirely sure what is going on.  I have read others have gotten this same card working with no problems, so it shouldn't be support for the card.  I typically don't use the PPA (Synaptic) to install the NVIDIA drivers and I'm not sure if that is the problem in this situation.  You could try installing the newest drivers based on the thread linked below.  Best of luck...

[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

> **heavy metal said:**
> Gibsonking, try to use the "hardware drivers" option, it can look if there's a driver for your Nvidia or you can try ubuntu 9.10 or wait a few days until the release of Lucid Linx, I have read there will be a new driver for Nvidia PC's in Lucid Linx, I think it will be called Noveau driver or something like that...


P.S. Remember, before you use Hardware drivers option you must run update manager and update ubuntu first...

Another thing, if you are interested in still using ubuntu and you are considering buying a new PC buy a motherboard with an Intel video chipset like the G31 or G41 my pc is using the G41 and it works very good, these chipsets have the best support for ubuntu...
Thank you for the thread, I will try that.




Hardware drivers comes up with nothing, and I have all of the updates installed.


Also, I plan on using this for F@H, some light gaming, and as a server. So while I have the G31 chipset, it just doesn't have enough power for what I want to do.

---

### Post by Objekt on 2010-04-14
I think this is a bug common to Ubuntu 8.04.3 and 8.04.4 LTS releases with Nvidia video hardware.  I also did not get Nvidia drivers showing up under "Hardware Drivers," even after installing 8.04.4 LTS and running apt-get update.

I tried installing manually-downloaded Nvidia drivers as well.  The Nvidia .run package appeared to complete successfully, but Ubuntu consistently came up in "low graphics," recovery mode after rebooting.

It only seems to happen with certain Nvidia hardware.  This January, I installed 8.04.3 LTS on a machine using a build-in Nvidia 3D chipset (GeForce 7025).  Hardware Drivers popped right up, offering to install the Nvidia binary driver package.  Go figure.

---

### Post by cK` on 2010-04-14
If your wiping and reinstalling trying to get it work why not upgrade to 9.10?

I have a 9800 GTX and system ->> administration -> hardware drivers
works like a charm. No problems.

Edit:: Dont "Upgrade" just burn the bootable iso image to a disk and do a fresh install from there.

I am ubuntu nub also, and i know how it feels trying to fix things when you do not know what your doing.

I would strongly recommend starting fresh with the newest version of ubuntu

[http://www.ubuntu.com/getubuntu/download]("http://www.ubuntu.com/getubuntu/download")

---

### Post by GibsonSGKing on 2010-04-14
> **cgb said:**
> Not entirely sure what is going on.  I have read others have gotten this same card working with no problems, so it shouldn't be support for the card.  I typically don't use the PPA (Synaptic) to install the NVIDIA drivers and I'm not sure if that is the problem in this situation.  You could try installing the newest drivers based on the thread linked below.  Best of luck...

[http://ubuntuforums.org/showthread.php?t=990978]("http://ubuntuforums.org/showthread.php?t=990978")

That thread worked like a charm. Thank you very much :)


EDIT: Great, another problem. Now, when I try to save the X config settings, it gives me this message:

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

Help please?

---

### Post by cgb on 2010-04-14
Do you get that error message at the end of the install process for the NVIDIA driver or what exactly are you doing when you get that?  A little confused on when this message is occurring.  

Also aside from that message does the card appear to be detected in the nvidia settings manager now?

---

### Post by steveneddy on 2010-04-14
> **GibsonSGKing said:**
> That thread worked like a charm. Thank you very much :)


EDIT: Great, another problem. Now, when I try to save the X config settings, it gives me this message:

"Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'."

Help please?

That's not an issue. The software won't/can't remove a simple backup file - no prob. It won't hurt anything.

If the video drivers are installed, continue using Ubuntu and enjoy.

Cheers

FYI - read the links in my sig for more Ubuntu info.

---

### Post by GibsonSGKing on 2010-04-14
> **steveneddy said:**
> That's not an issue. The software won't/can't remove a simple backup file - no prob. It won't hurt anything.

If the video drivers are installed, continue using Ubuntu and enjoy.

Cheers

FYI - read the links in my sig for more Ubuntu info.
Yeah, but now I have to change my display settings every time I boot.
> **cgb said:**
> Do you get that error message at the end of the install process for the NVIDIA driver or what exactly are you doing when you get that?  A little confused on when this message is occurring.  

Also aside from that message does the card appear to be detected in the nvidia settings manager now?

It appears only when I try to change the settings and save them, in the nvidia settings panel. I'm unsure how I can save them now :?


While I'm at it, I can't get it to display in 1920x1080; only 1680x1050 will work :S

---

### Post by cgb on 2010-04-15
you could try manually editing your xorg.conf file.  Below is a link I found for some generic instructions on the process.  Basically you will need to add "1920x1080" to the modes section and adjust any other settings according to your monitors capabilities.  

[http://ubuntuforums.org/showthread.php?t=1251114]("http://ubuntuforums.org/showthread.php?t=1251114")

---

### Post by mothes on 2010-05-02
Hello everybody! 

I've got the next problem, I tried to install official last graphic driver from NVIdia but I did not. This what I did: 

I just installed fresh and latest version of Ubuntu 10.04.
I tried to install the official last driver for graphic card GeForce 8600.
I installed the next packages:

```
# sudo aptitude install linux-headers-`uname -r`
# sudo aptitude install build-essential
# sudo aptitude install xserver-xorg-dev
# sudo apt-get install nvidia-settings

```
After I stoped GDM:
```
# sudo /etc/init.d/gdm stop

```
Update driver:
```
# su root
# sh NVIDIA-Linux-x86-195.36.07.04-pkg1.run --update

```
Install driver:
```
sh NVIDIA-Linux-x86-195.36.07.04-pkg1.run

```
And I've got the next error:
THE DISTRIBUTION-PROVIDED PRE-INSTALL SCRIPT FAILED.

In logs I've found:
UNABLE TO LOAD nvidia.ko the kernel module

Please help to solve this problem!

BUG about this problem is here [https://bugs.launchpad.net/ubuntu/+bug/572430](https://bugs.launchpad.net/ubuntu/+bug/572430)

---

### Post by dino99 on 2010-05-02
why ubuntu devs fine tuned drivers for our distro ?

stop whining  :lolflag:

---

### Post by Linuxforall on 2010-05-02
> **mothes said:**
> Hello everybody! 

I've got the next problem, I tried to install official last graphic driver from NVIdia but I did not. This what I did: 

I just installed fresh and latest version of Ubuntu 10.04.
I tried to install the official last driver for graphic card GeForce 8600.
I installed the next packages:

```
# sudo aptitude install linux-headers-`uname -r`
# sudo aptitude install build-essential
# sudo aptitude install xserver-xorg-dev
# sudo apt-get install nvidia-settings

```
After I stoped GDM:
```
# sudo /etc/init.d/gdm stop

```
Update driver:
```
# su root
# sh NVIDIA-Linux-x86-195.36.07.04-pkg1.run --update

```
Install driver:
```
sh NVIDIA-Linux-x86-195.36.07.04-pkg1.run

```
And I've got the next error:
THE DISTRIBUTION-PROVIDED PRE-INSTALL SCRIPT FAILED.

In logs I've found:
UNABLE TO LOAD nvidia.ko the kernel module

Please help to solve this problem!

BUG about this problem is here [https://bugs.launchpad.net/ubuntu/+bug/572430](https://bugs.launchpad.net/ubuntu/+bug/572430)

Works fine with this method here [http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)

---

### Post by lidex on 2010-05-02
Why not just install nvidia-current through synaptic? Too easy?

---

