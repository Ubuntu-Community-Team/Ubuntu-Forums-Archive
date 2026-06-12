---
title: "Kernel Upgrade: 386-&gt;686 SMP - Hangs on Boot"
date: 2006-04-06
forum: General Help
---

### Post by mozetti on 2006-04-06
Howdy,

Been running Breezy for a couple weeks and was so proud of myself for not having to post a thread yet ... then I decided to update Nvidia drivers & upgrade to the kernel optimized for my chip. And, here I am. :)

_Specs:_
[MSI 865PE Neo 2 LS](http://www.msicomputer.com/product/p_spec.asp?model=865PE_Neo2-LS&class=mb)
Pentium IV 2.6 Ghz, 800 FSB, Hyper-threading
Linksys WMP54G WiFi card with Ralink RT2500 chip
GeForce4 Ti4200 128MB AGP

_What I did:_
Install Ubuntu (used CAT-5 for connectivity) - Success
Get WiFi working - Success
Upgrade Nvidia drivers using [tseliot's guide - Method 2](http://ubuntuforums.org/showthread.php?t=75074) - Failure: I didn't know 'uname -r' was a bash command, so when I got to this instruction:
```
sudo apt-get --purge remove linux-restricted-modules-`uname -r
```

I put it in exactly, and of course it couldn't find a package named "linux-restricted-modules-uname-r", but I pressed on anyhow, thinking, "It can't be that bad, right?" (I know, I know -- I'm an idiot for this part.)

Anyhow, I got the new drivers installed. But when I restarted, X/Gnome wouldn't start because I didn't have the right linux-restricted modules. So, from the command line I used [Method 1 from tseliot's guide](http://ubuntuforums.org/showthread.php?t=75074) to install the nvidia drivers & linux restricted modules from the repos. - That worked.

So, at this point I'm back with a working Ubuntu/Gnome, but I want to use the latest Nvidia drivers and figured out my 'uname -r' mistake. But, I also want to upgrade the kernel. Logically, I figured I should upgrade the kernel to 686-smp first, then install the latest Nvidia drivers the correct way.

First, I installed the 686-smp kernel through command line apt-get:
```
sudo apt-get install linux-...-686-smp.
``` Restart, I see it updated Grub so I choose the new kernel. It gets to the stage of "Synchronizing clock with ntp.ubuntu...." and locks. Hard reboot. Try 686-smp recovery mode - same result.

I boot back into 386 and check the clock settings. When I tried to enable "Periodically sync with internet servers" it said I didn't have NTP installed, so I installed it. Reboot - 686/686-recovery - same result.

So, I read on the forums how to remove the ntp sync from startup (rcpi.d -remove ntpdate, something along those lines). I did that. Reboot - 686/686-recovery - now it stalls at setting up ICE socket directory or setting system clock. Hard reboot.

Now, I boot back into 386 and re-install 686-smp & its associated headers using Synaptic. Reboot - 686/686-recovery - same result.

I haven't done much customizing so far, basically just testing and updating a few things. One thing that did happen sporadically was related to the networking through WiFi - I don't know if this is part of my current boot problems or not: Not every time, but more than once, when it would start loading modules it would get stuck at initializing the network adapter, drop from the splash screen to the terminal and continue to boot after a minute or so of waiting for the network adapter.

1) I think I read that the ICE sockets directory is related to X. Are my 686-smp boot problems related to my hosed Nvidia driver upgrade?

2) Should I just start fresh, re-install Ubuntu, and start updating again?

3) If I do a fresh install, do I upgrade my kernel to 686-smp first, and then upgrade the Nvidia drivers? Or, do I upgrade the Nvidia drivers first, and then upgrade to the 686-smp kernel?

Thanks for all the help I've received through past forum posts, and for any help recieved here.

---

### Post by dcstar on 2006-04-06
[QUOTE=mozetti]
.......
First, I installed the 686-smp kernel through command line apt-get:
```
sudo apt-get install linux-...-686-smp.
``` Restart, I see it updated Grub so I choose the new kernel. It gets to the stage of "Synchronizing clock with ntp.ubuntu...." and locks. Hard reboot. Try 686-smp recovery mode - same result.
.......[/QUOTE]
Firstly, just install the non-SMP kernel available in Synaptic, secondly if your internet connectivity is not working 100% correctly then the boot up will pause at that point for over a minute, not "lock", did you wait for it to carry on?

---

### Post by mozetti on 2006-04-06
[QUOTE=dcstar]Firstly, just install the non-SMP kernel available in Synaptic[/QUOTE]

My processor has hyperthreading - without the SMP kernel, it won't take advantage of that.

[QUOTE=dcstar]secondly if your internet connectivity is not working 100% correctly then the boot up will pause at that point for over a minute, not "lock", did you wait for it to carry on?[/QUOTE]

*EDIT* I misunderstood what you were saying */EDIT*

I know. And yes, I did wait for it for approximately 5 minutes. But, even after I removed the ntp update from the boot process, it would hang at another point - the ICE sockets directory.

---

### Post by mozetti on 2006-04-06
Gimme a "B"!

Gimme a "U"!

Gimme an "M"!

Gimme a "P"!

---

### Post by mozetti on 2006-04-07
[QUOTE=mozetti]Gimme a "B"!

Gimme a "U"!

Gimme an "M"!

Gimme a "P"![/QUOTE]

What's that spell???

[SIZE="5"]BUMP![/SIZE]

*Last one, I promise. I'd just like to get some help on this if anyone has some insights. :)

---

### Post by mozetti on 2006-04-11
If anyone checks back here, the problem was the legacy drivers for my RaLink RT2500 WiFi card. Apparently these drivers don't work with SMP kernels.

---

### Post by mittio on 2006-04-12
[QUOTE=mozetti]If anyone checks back here, the problem was the legacy drivers for my RaLink RT2500 WiFi card. Apparently these drivers don't work with SMP kernels.[/QUOTE]

Good to know.  Any solutions on the horizon?

---

