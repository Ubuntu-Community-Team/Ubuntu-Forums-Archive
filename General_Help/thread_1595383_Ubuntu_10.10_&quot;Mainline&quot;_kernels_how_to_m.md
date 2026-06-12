---
title: "Ubuntu 10.10 &quot;Mainline&quot; kernels: how to manually install the Nvidia X driver ??"
date: 2010-10-13
forum: General Help
---

### Post by troutrou on 2010-10-13
Hi all,

I am trying to shake the bugs out of 10.10. My TV card, which uses the bttv driver, doesn't work any more since switching from 9.04 to 10.10.

The GUI stuff is not at fault it seems, so must be either the kernel or bttv module. 

Following guidance from the wiki, I installed a "mainline" kernel, to see if that makes any difference. THe problem is taht by doing so, the Nvidia driver stopped working, so no GUI hence can't test the TV !
I reverted to the Nouveau driver, which works, but sadly the TV apps don't like this driver, they all either fail to start, or start then freeze.

So I would need to install the Nvidia driver on this "Mainline"/debug kernel. I downloaded the installer for the latest driver, from nvidia's website, then proceeded.  
At first it complained that Nouveau was running, so I tried to "modprobe --remove nouveau" it, but it failed, sayting it was in use ! Weird, alwyas worked in the past :-(
The nvidia installer suggestes that adding a file in  /etc/modprobe.d to blacklist it at boot, might do it.  So I let it do that, then rebooted. I still see nouveau related messages in the kernel log, but somehow the Nvidia installer doesn't complain anymore about it, so let's assume this part is ok.

The problem now is that it complains that there is a GCC mismatch, says the kernel was built with 4.2 but something else relates to 4.4, so it fails to build the driver :-(

Been years since I had to get my hands dirty to get Ubuntu running... can anyone tell me how to get this driver to work on this mainline kernel ? I did download/install the kernel headers to go with it, of course, so no problems there I would think.

Thanks in advance...

---

