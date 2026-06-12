---
title: "Deleted ALSA drivers! Please Help..."
date: 2010-11-02
forum: General Help
---

### Post by Apurva Misra on 2010-11-02
Hi!
I am using 10.10 (Maverik)
I tried to install the RealTek Audio Driver available for linux on their site. There was a script to take care of all compilation and copying of compiled modules. However, the "make" in the script failed and the modules were not built. However, instead of exiting for the error, the script went on to delete everything in 

[FONT="Arial"]/lib/modules/$kaversion/kernel/sound/pci 
/lib/modules/$kaversion/kernel/sound/acore
/lib/modules/$kaversion/kernel/sound/core
($kaversion=`uname -r`; in my case,2.6.35-22-generic)
[/FONT]
In order to restore the modules, I tried the following:
1. [FONT="Arial"]sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils followed by sudo apt-get install linux-sound-base alsa-base alsa-utils. [/FONT]
But that did not restore the modules.

2. downloaded the alsa source and tried to compile it:
[FONT="Arial"]sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
followed by ./configure and make in the directory where i extracted the alsa source[/FONT]. It exits with the following error:

[FONT="Arial"]In file included from include/linux/pci.h:58,
                 from /home/am/tmp/modules/alsa-driver/acore/memalloc.inc:13,
                 from /home/am/tmp/modules/alsa-driver/acore/memalloc.c:1:
/home/am/tmp/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error: @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory
compilation terminated.[/FONT]

Please help me in restoring the modules...

---

### Post by josemi on 2010-11-07
if you have hardware audio checked with --> $lspci -v
and dont have device hardwares with --> $aplay -l 
try this -->$sudo modprobe snd-
here tab and choose a module like -->$sudo modprobe snd-usb-audio
if get errors... try the rest of post.

An old bug is around with all verisons of ubuntu and alsa

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/125](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/125)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/133](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200338/comments/133)

trying the last post i solve your/mine issue making:

a) goto system --> Synaptic

b) sort by name packages

c) look for

linux-backports-modules-alsa-2.6.35.22-generic (or your version kernel --> uname -r)
linux-image-generic

d) check for reinstall and apply

when done into command line type

e) $sudo depmod -a

f) now reboot the system

and now go to install/desinstall alsa but in any moment the modules dont load... so come here ang reinstall the modules again.

Saludos,
José Miguel

---

