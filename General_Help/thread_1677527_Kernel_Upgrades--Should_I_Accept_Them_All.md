---
title: "Kernel Upgrades--Should I Accept Them All?"
date: 2011-01-28
forum: General Help
---

### Post by casparov on 2011-01-28
Hi, Everyone...  

I am using Meerkat w/ the 2.6.35.24 kernel.  I am extremely satisfied w/ the direction of Ubuntu and Canonical and am amazed at the focus and dedication of all involved, including the contributors and moderators here.

But I have a question regarding continually upgrading the distribution kernels while awaiting the next iteration (11.04).  Is it advisable to upgrade every kernel when my system seems to run well without them?  For instance, each kernel upgrade necessitates that I reinstall the NVIDIA driver, among a couple other minor problems.  This is not that big a deal, but I would like to avoid it--it's just an irritation when I reboot to a black screen.  But another irritation is continually ignoring the update notices.

I would like to hear anyone's opinion.

Thanks so much for your reading this,

Casp

---

### Post by djeikyb on 2011-01-28
Not to mention ruining grub. I like to see what happens when I boot, so I delete the quiet option from grub entries. Updating the kernel means I have to do that work all over again, every @#$%ing time.

---

### Post by mrhhug on 2011-01-28
i treat my distro upgrades like i treat embedded firmware. Don't upgrade unless you have a reason to upgrade.

i like to stick the the LTS releases and rarely upgrade in between. unless you have a system then needs the most uptodate security why would you go through reinstalling graphics drivers every few months.

why fix it if it aint broke? i've turned off automatic update notifications all together in some situations.

---

### Post by clhsharky on 2011-01-28
casparov


May I suggest updating once a month as a compromise with updates and convenience.

Many users like to update proprietary drivers once a month when they are released, and that is a excellent time to update OS.

1- uninstall old video driver
2- update OS on open source driver
3- install new video driver
reboot after each step

This may not be perfect for all, but less breakage with updates is also important to some.


Sharky

---

### Post by casparov on 2011-01-29
Gosh, thanks, you guys...

I thought that everyone just, sort of, reflexively accepted these new kernels w/o a hitch.

If I can I will wait for the big one, 11.04...  

Casp

---

### Post by uRock on 2011-01-29
I constantly run updates. If a kernel update gives any problems, then just revert to the most recent working kernel.
Updates have never broke my system.

---

### Post by casparov on 2011-01-29
But you have 4,000 beans!!!    C.

---

### Post by uRock on 2011-01-29
> **casparov said:**
> But you have 4,000 beans!!!    C.
My bean count means that I talk alot. :P

---

### Post by robert shearer on 2011-01-29
> **uRock said:**
> My bean count means that I talk alot. :P

:lolflag:

---

### Post by PRC09 on 2011-01-29
> If I can I will wait for the big one, 11.04... 

If I am not mistaken to do an UPGRADE to 11.04 you will need need to bring everything up to current status before you can anyway.Could be a chore if you need to update 3 or 4 kernels to do it.....

---

### Post by Krytarik on 2011-01-29
@casparov: To avoid the mandatory re-install of the video driver, you could choose to install those via "System -> Administration -> Additional Drivers". Remove the manually installed one before, following the install instructions. If you really need to run the most recent driver, try Ubuntu-X-Swat's PPA:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

@djeikyb: I recommend setting the boot options in "/etc/default/grub" instead of "/boot/grub/grub.cfg" itself, the value of "GRUB_CMDLINE_LINUX_DEFAULT" is relevant for you.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

And yes, I apply each kernel upgrade, I don't want to care about any possible security holes, you never know.;)

Greetings.

---

### Post by uRock on 2011-01-29
> **PRC09 said:**
> If I am not mistaken to do an UPGRADE to 11.04 you will need need to bring everything up to current status before you can anyway.Could be a chore if you need to update 3 or 4 kernels to do it.....
With the major change in the GUI I would recommend a clean install over upgrade.

---

### Post by casparov on 2011-01-29
Krytarik...

Thanks for that hint--I will look into that.

(I hope things are well in Berlin.)

C.

---

### Post by Krytarik on 2011-01-29
> **casparov said:**
> 
(i hope things are well in berlin.)

8-)

---

### Post by JKyleOKC on 2011-01-29
Since many kernel updates are to fix potential security problems, I do install them all. To eliminate the black-screen situation with my Nvidia drivers, I do not do the immediate restart that the update routine wants. Instead, I open Synaptic Package Manager, search out the linux-header packages for the new kernel version, mark them to be installed, and click apply. (I usually also mark the oldest installed kernel packages for complete removal, to keep only the new one and the immediately-prior one on my system.) Only after the header package has installed do I click the "restart" icon.

During the restart process, the DKMS package (which I installed many months ago, again via Synaptic) cuts in and rebuilds all of the kernel modules needed by Nvidia and VirtualBox automatically. It slows things down a bit during that first restart but only happens the one time.

As for seeing the boot text rather than watching the splash screen, I've edited my /etc/default/grub file to remove the "quiet splash" options from the menu, so it doesn't change with the kernel update even though update-grub does run.

---

### Post by dFlyer on 2011-01-29
I always update as they become available.

---

### Post by casparov on 2011-01-31
JKyleOKC (and all others)...

Thanks so much, again, for your time and your valuable insights.

I truly appreciate all your help and have acted on each bit of advice.  (JKyle--that includes downloading many headers through synaptic.  I'll wait to see what happens.)

All Regards,   C.

---

