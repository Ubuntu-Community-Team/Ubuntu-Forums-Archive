---
title: "Ubuntu under VMware: how to select 1024x600 resolution?"
date: 2009-10-20
forum: General Help
---

### Post by HerrKaputt on 2009-10-20
Hi folks, complete Ubuntu rookie speaking :)

I am using Ubuntu 9.04 as guest OS under VMware Workstation 6.5 (host is Windows XP Home). The host has a screen size of 1280x800, and I'd like the guest to have 1024x600 size to fit on the screen. That resolution is not available under System > Preferences > Display.

I have already tried searching around for ways to do this, and I've managed to use xrandr to add a new mode to my "default" screen. Here's the output of the xrandr command:

```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2360 x 1770
default connected 1280x800+0+0 0mm x 0mm
   800x600        60.0     56.0      0.0  
   640x480        60.0      0.0  
   320x240         0.0  
   400x300         0.0  
   512x384         0.0  
   1024x768        0.0  
   1152x864        0.0  
   1280x960        0.0  
   1400x1050       0.0  
   1600x1200       0.0  
   1920x1440       0.0  
   2048x1536       0.0  
   854x480         0.0  
   1280x720        0.0  
   1366x768        0.0  
   1920x1080       0.0  
   1280x800        0.0* 
   1440x900        0.0  
   1680x1050       0.0  
   1920x1200       0.0  
   720x480         0.0  
   720x576         0.0  
   320x200         0.0  
   640x400         0.0  
   800x480         0.0  
   1280x768        0.0  
   1280x1024       0.0  
   2360x1770       0.0  
  1024x600 (0x12d)   49.0MHz
        h: width  1024 start 1072 end 1168 total 1312 skew    0 clock   37.3KHz
        v: height  600 start  603 end  613 total  624           clock   59.9Hz
```

As you can see I managed to add the 1024x600 mode. If I then do

```
$ xrandr --output default --mode 800x600
```

I manage to change the resolution, but if I do the same for the 1024x600 resolution I get

```
$ xrandr --output default --mode 1024x600
xrandr: cannot find mode 1024x600
```


I'm pretty confused at the moment. What am I doing wrong? Any help is appreciated, thanks in advance!

---

### Post by P4man on 2009-10-20
try this:

```
xrandr --newmode "1024x600" 49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
```

then

```
xrandr --addmode VGA 1024x600
xrandr --output VGA --mode 1024x600
```

That said, doesnt VMware have something like virtualbox guest additions which installs (virtual) videodrivers in the client?

---

### Post by sandy8 on 2009-10-20
Hi P4man
I am new to Linux OS and facing same problem but instead of Ubuntu I have installed RHEL in dual boot mode with Window Xp. I have not found solution of this problem yet.
If you can help me out, please reply. Thanks in advance.

---

### Post by P4man on 2009-10-20
> **sandy8 said:**
> Hi P4man
I am new to Linux OS and facing same problem but instead of Ubuntu I have installed RHEL in dual boot mode with Window Xp. I have not found solution of this problem yet.
If you can help me out, please reply. Thanks in advance.

I dont know the first the thing about red hat, and if you havent installed the OS on a virtual machine, the solution is probably elsewhere (in the videodrivers)

---

### Post by sandy8 on 2009-10-20
Hi P4man.
I am also a Linux user and facing same problem but still can't find its solution. I have installed RHEL 4 in dual boot mode with Windows Xp. Please, reply quickly.

---

### Post by HerrKaputt on 2009-10-20
> **P4man said:**
> try this:

```
xrandr --newmode "1024x600" 49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
```then

```
xrandr --addmode VGA 1024x600
xrandr --output VGA --mode 1024x600
```That said, doesnt VMware have something like virtualbox guest additions which installs (virtual) videodrivers in the client?

Thanks for the help P4man,

I tried what you suggested. The "--newmode" command works fine, but when I try the "--addmode" command I get

```
$ xrandr --addmode VGA 1024x600
xrandr: cannot find output "VGA"
```


EDIT: I tried a slight variant of your suggestion, since my output is named "default" and not "VGA". What I got was

```
$ xrandr --addmode default 1024x600
$ xrandr --output default --mode 1024x600
xrandr: Configure crtc 0 failed
```


So I managed to get a different error message this time, but I am as baffled as before... any help is appreciated. Thanks!

---

### Post by kpholmes on 2009-10-20
i dont know about vmware but in virtual box by sun micro you can mount a virtual cd called "guest additions" that make running the guest os alot smoother, is there any option like that?

---

### Post by HerrKaputt on 2009-10-20
> **kpholmes said:**
> i dont know about vmware but in virtual box by sun micro you can mount a virtual cd called "guest additions" that make running the guest os alot smoother, is there any option like that?

Yes, there's something called "VMware Tools" that you can install on the guest OS for that. I already installed it on my guest Ubuntu system.

---

### Post by P4man on 2009-10-20
I dont know. I figure its a problem with the VM? Then again Im not xrandr expert by any stretch of the imagination. 

The only suggestion I can make is use virtualbox as VM, then you can install the ubuntu guest additions which provides a seamless environment where you can move your mouse in and out the vm and resize the VM window automatically resizing the client VMs "resolution". Virtualbox is free and its absolutely fabulous (although I use it the other way, to virtualize windows on an ubuntu host).

---

### Post by P4man on 2009-10-20
> **HerrKaputt said:**
> Yes, there's something called "VMware Tools" that you can install on the guest OS for that. I already installed it on my guest Ubuntu system.

Ah missed that. my best guess is that those tools do not support the resolution you want.

---

### Post by HerrKaputt on 2009-10-20
I'll ask for help from one of the IT staff at work (I wanted to try and solve this myself first).

I will also try virtualbox as per your suggestion, and will post back the results. Thanks for your help!

---

