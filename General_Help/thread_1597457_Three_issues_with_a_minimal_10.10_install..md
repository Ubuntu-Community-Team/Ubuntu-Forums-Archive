---
title: "Three issues with a minimal 10.10 install."
date: 2010-10-15
forum: General Help
---

### Post by FallenUnia on 2010-10-15
Hello all,

I just installed a minimal version of Ubuntu 10.10 (with Openbox) over 10.04. Mainly everything's ok, but I have three problems:

1. When shutting down or rebooting, my speakers make a loud pop. Upon googling around, I found [this](https://bbs.archlinux.org/viewtopic.php?pid=811795) topic on the Arch forums. Running ```
modprobe -r snd-hda-intel
``` before rebooting/shutting down works. I, however, would like to have this permanently fixed so I don't have to run these commands every time before rebooting/shutting down.
2. I can't install the ATi video card drivers. I downloaded the correct driver (10.9) from the ATi website and made sure I had the packages found [here](http://crunchbanglinux.org/forums/topic/8992/how-to-install-ati-catalyst-control-center-ati-drivers-for-x64/) installed. I also made it executable by running ```
chmod +x ati-driver-installer-10-9-x86.x86-64.run
```When I run the installer, using ```
sh ati-driver-installer-10-9-x86.x86-64.run
``` I get this output:
```
jente@Lappy:~/Downloads$ sudo sh ati-driver-installer-10-9-x86.x86_64.run
Created directory fglrx-install.KMpo6O
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.KMpo6O
jente@Lappy:~/Downloads$ 

```
What's going on?
3. When booting, I get a message saying something like "intel_ips can't find i915 symbols, so graphics turbo is disabled". When googling for this, I see this is a kernel related issue. Since I don't have any understandings of kernels, I thought this is a little too high up for me. What does it mean and how can I fix it, as it slows my boot down quite a bit?

Thanks in advance.

---

### Post by archanmishra on 2010-10-15
Hello all,

I too am facing Problem similiar to 
issue 2. i.e. 
my graphics card driver is giving the error

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being

i have an ATI radeon HD4570 card on a dell studio 1555 , using maverick 64 bit.

---

### Post by ashwinhgtx on 2010-10-16
> **archanmishra said:**
> Hello all,

I too am facing Problem similiar to 
issue 2. i.e. 
my graphics card driver is giving the error

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being

i have an ATI radeon HD4570 card on a dell studio 1555 , using maverick 64 bit.

Have you tried using the Additional Drivers utility that comes with Ubuntu to install the ATI drivers?

---

### Post by FallenUnia on 2010-10-17
^ Thanks, but that doesn't apply to me. Anyone else?

---

### Post by Zookalicious on 2010-12-09
For problem 1, you can add that line to your startup applications file which is located in /home/username/.openbox (I don't recall which EXACT file, since it's been awhile since I've used *box WM's...) If that isn't enough info let me know and I can clear that up a bit (I'm just in a rush right now :P )

---

### Post by rrsodl on 2010-12-16
> **archanmishra said:**
> Hello all,

I too am facing Problem similiar to 
issue 2. i.e. 
my graphics card driver is giving the error

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being

i have an ATI radeon HD4570 card on a dell studio 1555 , using maverick 64 bit.


Hi,

Download the correct version for 10.10 from here [http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10](http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10)

That solved the problem for me.

---

