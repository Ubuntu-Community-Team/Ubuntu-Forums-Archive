---
title: "untimely reboots after upgrade to 10.4"
date: 2010-05-29
forum: General Help
---

### Post by annec on 2010-05-29
Hi there,

Since I upgraded to 10.4, the laptop keeps rebooting. It doesn't seem like a specific program is causing this. It sometimes happens when using firefox, other times with vlc. 

The reboots occur once to twice a day, randomly I believe.

I should probably add that the upgrading procedure did not go without problems : I started through the update manager but it stopped in the middle. I launched it again through the terminal (apt-get upgrade I think). Anyway this second time it seemed to work fine. 

I don't think of further informations I could provide. I may not ask myself the right questions. 

Could somebody please help me diagnose this problem? 

Thanks a lot!

---

### Post by lavinog on 2010-05-29
Are you using a proprietary driver (nvidia or ati)?

Is it actually restarting or is the graphical session restarting (do you get the full boot, or does it seem to happen quickly)

The log file viewer in the administration menu is a good place to start.  Try looking in kern.log and messages, and look at the time that a reboot happened.

---

### Post by annec on 2010-05-29
Thanks for you quick answer!

Actually, my description was not accurate : it does not reboot, the computer just shuts down! 

And thanks to your advices, I think I found the problem in the kern.log messages: "Critical temperature reached (105 C), shutting down."

So it's a hardware problem it seems. It's true that the laptop sometimes becomes terribly hot and noisy. Of course that happens mostly when many programs run. Now I recall it once shut down while I was executing a large memory requiring Matlab script. However I'm under the impression that it uses a lot of resources for simple tasks too. 

Plus what puzzles me is that the shutting down part  didn't happen with previous versions of Ubuntu.

OK, so, problem diagnosed, but not solved yet. Can you think of something I could do?

Thanks again!

---

### Post by lavinog on 2010-05-29
What video card do you have.

There are a couple of things that can cause it to overheat.  There are many other users that have reported similar issues.

For ATI: the opensource ati driver does not have any power saving features enabled and can increase the temperature of the heatsink that also cools the cpu.

Is this an intel processor or a AMD processor?

---

### Post by annec on 2010-05-29
The processors are listed as : 
Processor(0) : Intel Pentium Dual CPU T3400 @2.16GHz
Processor(1) : Intel Pentium Dual CPU T3400 @2.16GHz

For the graphics card, lspci gives me : 
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

Actually I have no idea what kind of stuff this is :) I definitely wouldn't define myself as an expert!

---

### Post by lavinog on 2010-05-29
Make sure you have the latest updates. (administration > update manager)

This bug report might be related:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281)

---

