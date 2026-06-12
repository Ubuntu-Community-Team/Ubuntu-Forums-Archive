---
title: "Issue with waking from sleep mode"
date: 2010-05-07
forum: General Help
---

### Post by jeffrey2009 on 2010-05-07
Computer using Ubuntu 10.04 not able to come out of sleep mode.  I try to hit the keyboard or move mouse and can't get the computer out of sleep mode.  The computer light just stays on blinking, please advise.  Seems like there were a lot of others who had this problem.  

[http://ubuntuforums.org/archive/index.php/t-1138178.html](http://ubuntuforums.org/archive/index.php/t-1138178.html)

---

### Post by jerenept on 2010-05-07
Press the power button.

---

### Post by Solinoure on 2010-05-07
I have the same issue.

---

### Post by jeffrey2009 on 2010-05-08
The requirement is to have normal wake behavior which is for the system to wake after the user clicks the keyboard or moves the mouse.

I did see some things about using quirk checker but I could not find this software.

[http://ubuntuforums.org/showthread.php?t=1281130](http://ubuntuforums.org/showthread.php?t=1281130)

---

### Post by sgage on 2010-05-08
Are you using an NVIDIA graphics card? I could never get my computer to wake from sleep with the default nouveau drivers, but it works perfectly with the proprietary nvidia drivers.

---

### Post by zacktu on 2010-05-08
I agree with #2.  Before trying something complex, just click the power button.  Thus far, it has worked every time.

---

### Post by pmos69 on 2010-05-08
> **jeffrey2009 said:**
> Computer using Ubuntu 10.04 not able to come out of sleep mode.  I try to hit the keyboard or move mouse and can't get the computer out of sleep mode.  The computer light just stays on blinking, please advise.  Seems like there were a lot of others who had this problem.  

[http://ubuntuforums.org/archive/index.php/t-1138178.html](http://ubuntuforums.org/archive/index.php/t-1138178.html)

File a bug, or mark a current one as affecting you also.
Here's one I filed: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568711)

Try to diagnose it first: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by ayampanggang on 2010-05-08
> **sgage said:**
> Are you using an NVIDIA graphics card? I could never get my computer to wake from sleep with the default nouveau drivers, but it works perfectly with the proprietary nvidia drivers.


in my case with ATI card, suspend doesn't wake with the proprietary fglrx driver so i used the open source radeon driver.it now works for me about 90% of the time.

---

### Post by jeffrey2009 on 2010-05-26
well then if I am supposed to hit the power button then there is no point into going into sleep mode.  I suppose I should just shutdown.  Isn't this bad for the system to shutdown and restart on a daily basis?  Plus it takes a little longer.  Just looking to optmize here.

---

### Post by jeffrey2009 on 2010-05-26
I have graphics card:

 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)

---

### Post by jeffrey2009 on 2010-05-26
How do i change this?  How to know which driver to use?  I guess I could use the one you used.  I also have another quirky thing with my monitor it seems to flicker every once in a while.  I think there is an issue with my graphics card driver as you said. What to do next?

---

### Post by harshads on 2010-05-27
I've been having very similar problems.

My laptop will go to sleep just fine - I have it configured to go to  sleep only when I press the power button.

However, it doesn't recover properly more often than not. When I press  the power button to wake it up, the screen backlight comes on and I can  hear the HDD and the GPU fan start spinning. But the screen remains  blank and only way I can get my laptop to do anything is to force it off  and restart.

I am not able to pinpoint the exact cause of this.  Closing the laptop  screen and leaving it in sleep for a while both seem to cause the issue.  If I suspend and resume fairly immediately it recovers fine (prompts me  for my password and all)

I have used gconf-edit and changed everything relevant I could fing in  apps>gnome_power_manager. The system is behaving fine (and in  accordance with what I selected) except for this issue. 

I have a Dell studio 14z
It has an nvidia 9400 gpu and I have installed the latest drivers from  the nvidia site (this issue persists and existed even before I installed  them)
I am running Ubuntu Lucid as my only OS

Any fixes? Suggestions?

Edit: I have /home mounted in its own partition. I don't know how this  might affect anything.

Edit #2: I posted this in this thread - [http://ubuntuforums.org/showthread.php?p=9356145](http://ubuntuforums.org/showthread.php?p=9356145) Still haven't gotten a reply there

---

### Post by jeffrey2009 on 2010-05-27
Sorry I actually have a VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]

I looked up the driver on amd.com website and found one and tried to install
ati-driver-installer-9-3-x86.x86_64.run

but I get an error:
Created directory fglrx-install.URCRZX
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.URCRZX

---

### Post by jeffrey2009 on 2010-05-27
Are you saying that pressing the power button would get me out of suspend mode.  It seems not to work since the monitor stays black.  Although the state of the computer seems to change.

---

### Post by jerenept on 2010-05-27
Hmm... seems the GPU's are at fault here. When posting in this thread, pls tell us your GPU and the drivers installed.
BTW, sleep works just fine for me, nvidia-current installed, GeForce 6100/nForce 405
Even wakes up from sleeping overnight.

Maybe you should try the drivers in the 'Hardware Drivers' application.
System>Administration>Hardware Drivers.

---

### Post by bondo101 on 2010-05-28
this helped me I changed resolution a little lower,dell square 19" monitor  I also changed the driver to a different one listed in the drop down box.  Monitor was cutting off had to reboot and hold the on button untill the dell logo came up ,  Then everything is fine so far. I have an nvidia 6150 on board  card 512 of ram . I used the 173 driver versus the 183 driver in the driver menu. This problem just started lately . also i'm using karmic kolala.  Mabey this helps :KS  I know , but its not lucid but both of these distros seem to be having some of the same problems:KS

---

