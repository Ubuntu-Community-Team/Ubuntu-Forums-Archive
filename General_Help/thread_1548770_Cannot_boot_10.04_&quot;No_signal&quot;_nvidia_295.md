---
title: "Cannot boot 10.04 &quot;No signal&quot; nvidia 295"
date: 2010-08-08
forum: General Help
---

### Post by trjones on 2010-08-08
Greetings all.  I am at my wits end trying to get Kubuntu 10.04 working and am just about ready to give up and go back to 9.10.  I have a new work machine with a nVidia Quadro NVS 295.  I can boot from the live CD no problem.

 I can also install Kubuntu 10.04 without any issues.  I can also use the live CD without any trouble with my installed partition available, this requires no special parameters  However when I try to boot into the installed Kubuntu the screen displays a blinking cursor for a bit then the screen gives a "no signal" and that is that. 

I tried waiting for a bit and hitting CTRL+ALT+F2 to get into the command-line but that just displayed a nonsense string of ascii characters (some white, some colour, some blinking).  I have tried the following:  Editing the boot parameters to include "nomodeset" and "rescue". This hasn't worked.  

I have tried chrooting into the installed partition and installing the nvidia-current drives but this dies a death due to lack of internet connection. I tried downloading the nvidia-current drivers into the live CD partition and copying them (and the 2 dependencies) into the chroot and installing from there but that also dies due to MORE dependencies not being met.

If anyone has any idea how I can get into the command line for the installed system so I can try and get rid of the nouveau drivers and install the nVidia binary ones I am all ears.

I have tried looking around and this thread seems similar but nothing there helps.
[http://ubuntuforums.org/showthread.php?p=9648415](http://ubuntuforums.org/showthread.php?p=9648415)

This has been a hugely frustrating time, especially since I am installing this on a work computer in a company that is all windows. This is not giving Linux a good press.

---

### Post by trjones on 2010-08-08
Murphy's law of tech support says that after posting I naturally find the answer.

Ok, what I needed to do was:

Install Kubuntu
Remove the Live CD
Hold down shift when the computer prompts so that I get the grub boot menu
Scroll to the recovery option
hit "e" to edit the boot parameters
At the end of the line beginning with "linux" add "nomodeset"
In the next semi-graphical prompt choose to drop to root shell (Last option)
Set up the network in cmdline
install nvidia-current

Jesus, that was a complete faff. I am a linux fanboi but how the hell we expect a normal use to do that....

Makes me wonder if the nouveau drivers are good enough to be selected as the default.

---

### Post by jflaker on 2010-08-08
Does this machine have an onboard/integrated video card?  If so, disable it in BIOS......My 2 cents for now....

---

