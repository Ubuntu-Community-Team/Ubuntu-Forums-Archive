---
title: "libgl1-mesa-glx/dri Low graphics mode."
date: 2012-01-09
forum: General Help
---

### Post by beefheartvliet on 2012-01-09
Hi,

I wonder if anyone can help. I kind of know what's caysed the problem, but don't understand enough why and or how to rectify it without screwing my system. With that in mind, just a little bit of background. 

I'm Using Ubuntu 11.04 Dream Studio. 
I remember on a previous installation that Drivers libgl1-mesa-glx and dri caused a problem with x-org I assume.  So reinstalled. With that i mind for months now, ever time I see them I avoid installing them. However I installed them and now can only boot into my desktop in low graphics mode. I have an ATI Card and was using the ati-driver-installer-11-4-x86.x86_64.run as the Card driver. 
So needless to say once those two drivers installed I lost 3d functionality, and goes to a black screen on startup. No login screen. As I say I can get in in low gfx mode. 
The ATI Catalyst Control Centre is installed with errors. IE. I can start the GUI, and it reports that I can find details of the error here............

Installation complete.
There were errors during installation.  Details can be found in /usr/share/ati/fglrx-install.log


Here's the Error message. 



Creating symlink /var/lib/dkms/fglrx/8.841/source ->
                 /usr/src/fglrx-8.841

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cd /var/lib/dkms/fglrx/8.841/build; sh make.sh --nohints --uname_r=3.0.0-13-lowlatency --norootcheck.....(bad exit status: 1)
0
0
[Error] Kernel Module : Failed to build fglrx-8.841 with DKMS
[Error] Kernel Module : Removing fglrx-8.841 from DKMS

------------------------------
Deleting module version: 8.841
completely from the DKMS tree.
------------------------------
Done.
[Message] Kernel Module : update initramfs not required


I'd appreciate if any of you good folks can point me in the right direction as to how to rectify this. 

If I was to try and remove the two files Synaptic, it wants to uninstall ridiculous amount of stuff with it.  So thus far have resisted to do that thinking that there must be another way to sort it. 

I'll gladly try and provide any additional info you might need. 

Much appreciated

---

### Post by beefheartvliet on 2012-01-28
well after several weeks of putting up with starting in low graphics mode, I thought I'd have another shot at it. Either way I managed to install the ATI Catalyst Drivers with --force. I have also locked the two offending updates that caused the issue in the synaptic package manager. Everything is now back to how it was. I'm glad that people don't answer my post's in some regard :-)

---

### Post by kisi3l on 2013-01-02
What updates You locked in Synaptic ? I fighting with same problem from few hours.
.
Well, I have the same error but of course with newer fglrx driver (8.97.100.3).

I'm using Kubuntu 12.10 and I have Radeon HD4550.

I hope for quick reply.

---

