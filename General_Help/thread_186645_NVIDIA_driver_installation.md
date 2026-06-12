---
title: "NVIDIA driver installation"
date: 2006-06-02
forum: General Help
---

### Post by slimdog360 on 2006-06-02
Okay, Ive looked at a few threds so far and none of them seem to work. Ive used synaptic and that, I thought, worked but when I tryed to play foo billards it was incredibly slow, so I assumed they were not installed correctly.
 When I download the driver form the nvidia website and try to install it the way the say to do it, I get a message saying your running X server.. bla bla bla...exit X server and try again. I dont know what X server is let alone how to exit it, so my question is. 
Is there an easy way to install nvidia graphics drivers?
Thanks

---

### Post by _simon_ on 2006-06-02
This is by far the easiest I have found:

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

I've used it on 2 machines without an issue.

---

### Post by hobbit1983 on 2006-06-02
From what I remember once you have installed the packages from synaptic there is a command you need to run to "enable the drivers"  I can't remember exactly what the command is - however if you serach for nvidia in synaptic one of the packages states what the command is.

any pbms post back and I'll go and find the command for you

---

### Post by slimdog360 on 2006-06-02
I got it working, thanks for the help

---

### Post by FredB on 2006-06-02
I installed very simply a 3d enabled server for my nvidia GeForce FX 5200. With Synaptic, I installed nvidia glx server. After that, in a console, I typed sudo nvidia-glx-config enable, killed X (using ctrl+alt+backspace) and after X restarted, I had nvidia server launched ;)

---

### Post by FisherPrice on 2006-06-17
Hey, I don't know if this thread is being watched but I am tearing my hair out at the moment trying to get my NVIDIA FX 5200 (128M) working I have tried EVERYTHING that is currently on the posts, except [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper") Method two - I don't see how it is different from the script that was posted here. I ran the script, an abismal failure I'm sorry to say. The script ran fine I will add, however when I rebooted X came up with it's dreary black screen and locked the computer up. I am running on a WinFast motherboard with an SiS chipset. My lspci output is :-


0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
0000:00:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)



I've tried the simple commands that install the set of drivers from Ubuntu so PLEASE don't even bother telling me to "apt-get install nvidia-glx......" 'cause I won't believe you.

Can anyone help me PLEASE?

---

### Post by Rui Pais on 2006-06-17
Hi,
i simply downloaded NVIDIA-Linux-x86-1.0-8762-pkg1.run and run
sudo sh /usr/src/NVIDIA-Linux-x86-1.0-8762-pkg1.run 
everytime i compile a new kernel.

---

### Post by Seanz0rz on 2006-06-17
[QUOTE=Rui Pais]Hi,
i simply downloaded NVIDIA-Linux-x86-1.0-8762-pkg1.run and run
sudo sh /usr/src/NVIDIA-Linux-x86-1.0-8762-pkg1.run 
everytime i compile a new kernel.[/QUOTE]


what about all the packages that you need? (ie binutilits, etc)

i dont want to use the synamptic nvidia drivers, they suck imo and have never worked properly for me. i like the ones on nvidia's site, and want to use those, and did on breezy. im looking for my guide on how to install it on breezy, im assuming it cant be much different.

---

### Post by Rui Pais on 2006-06-18
[QUOTE=Seanz0rz]what about all the packages that you need? (ie binutilits, etc)

i dont want to use the synamptic nvidia drivers, they suck imo and have never worked properly for me. i like the ones on nvidia's site, and want to use those, and did on breezy. im looking for my guide on how to install it on breezy, im assuming it cant be much different.[/QUOTE]

Oh yes, the dependencies... i allways build my custom kernels, e17 from cvs and one or two apps that didn't exist on repos... so i guess i have all dependencies needed (to compile stuff, i mean). 
But shouldn't build-essential and gcc be all one needs? And at least all last drivers compiled well without the need to go to gcc 3.4 as i see mentioned in several times...

---

### Post by loserboy on 2006-06-21
when i try typing "sudo nvidia-glx-config enable"   

it says "Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

---

### Post by tseliot on 2006-06-21
[QUOTE=loserboy]when i try typing "sudo nvidia-glx-config enable"   

it says "Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."[/QUOTE]
Please follow my guide or try my script:
[http://ubuntuforums.org/showthread.php?t=139264]("http://ubuntuforums.org/showthread.php?t=139264")

---

