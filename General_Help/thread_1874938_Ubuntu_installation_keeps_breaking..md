---
title: "Ubuntu installation keeps breaking."
date: 2011-11-04
forum: General Help
---

### Post by murdockpt on 2011-11-04
So for the past few days ive been enjoying the hell out of Ubuntu 11.10. Got it installed, streamlined it a bit, got it going good...

then i decided to install the most up to date NVIDIA drivers.

I ctrl_alt_f2'd to the prompt, killed xserver (sudo stop lighdm or whatever the command is), went to the directory i had the driver file in and ran the .run (downloaded from the NVIDIA drivers site for Linux 32-bit. Probably not my brightest decision). I assumed the installation went well. Rebooted.

I have a dual-boot setup, chose to boot into Ubuntu like usual. Greeted by what looked like old school MSDOS mess. A few processes showing as [FAIL] (error report, starting lightdm, etc). Panic'd rebooted, knowing I broke my installation, or at least the drivers.

Couldnt find a way to revert back to the drivers that came with the installation (173 and recommended, whatever that version happened to be) so I wiped the partitions, rewrote the /boot /home and root partitions. Booted into Ubuntu from USB, installed (as in reinstalled the entire OS from scratch), rebooted and got the good old GRUB boot selection. Chose what I wanted and BAM...

Errors just like before.

I've done this twice, and have each time gotten the same results. So here I am. **_What should I do?_** 

It seems no matter what I do, I cant get it fixed. I cant get past the MSDOS-esque screen after the GRUB menu. No GUI, desktop, nothing. Just the confusing as hell text.




Note: In windows, Ive set up the dual boot using EasyBCD. The linux part is directed towards the 250mb /boot partition I made and had the boot directory installed to, in case that might be the issue right there.

Note2: When installing Ubuntu 11.10 through the USB, when I get to the point where it says to make sure i have space, connected power and an internet connection, something wierd happens. It has all 3 checked and ready, but when I press continue, it pauses, then places a gray X next to "is connected to the internet". I usually continue because as of now I cant figure out why its doing this (wired and wireless both connected to same router). Hopefully its not messing things up.

Note3: Noticed NVIDIA released new drivers today, not two hours after I installed what I thought was the most up-to-date.

Im going to go to sleep and Ill be back tomorrow to check solutions. This was a disastrous move and ive learned a pretty useful lesson. 

Note4: I have novice knowledge of Linux. Trying to make the transfer from windows to linux. Still learning the basics.

---

### Post by dcstar on 2011-11-04
> **murdockpt said:**
> So for the past few days ive been enjoying the hell out of Ubuntu 11.10. Got it installed, streamlined it a bit, got it going good...

then i decided to install the most up to date NVIDIA drivers.

I ctrl_alt_f2'd to the prompt, killed xserver (sudo stop lighdm or whatever the command is), went to the directory i had the driver file in and ran the .run (downloaded from the NVIDIA drivers site for Linux 32-bit. Probably not my brightest decision). I assumed the installation went well. Rebooted.

I have a dual-boot setup, chose to boot into Ubuntu like usual. Greeted by what looked like old school MSDOS mess. A few processes showing as [FAIL] (error report, starting lightdm, etc). Panic'd rebooted, knowing I broke my installation, or at least the drivers.

Couldnt find a way to revert back to the drivers that came with the installation (173 and recommended, whatever that version happened to be) so I wiped the partitions, rewrote the /boot /home and root partitions. Booted into Ubuntu from USB, installed (as in reinstalled the entire OS from scratch), rebooted and got the good old GRUB boot selection. Chose what I wanted and BAM...

Errors just like before.

I've done this twice, and have each time gotten the same results. So here I am. **_What should I do?_** 
........

Delete the partitions and then exit the install process and reboot, then see what the partition table shows.

---

### Post by murdockpt on 2011-11-04
> **dcstar said:**
> Delete the partitions and then exit the install process and reboot, then see what the partition table shows.

Im assuming you mean boot into ubuntu, delete the partitions, rebot into ubuntu and check what that area looks like, correct?

obviously cant kill off my windows 7 partitions.

---

### Post by haqking on 2011-11-04
Tip for the future, after a base install take a clone image of it if it is working using clonezilla or similar.

I take base images, driver update images and complete customised images.

I can drop back to anything i had in about 10 minutes at anytime i like.

So when you customise or add something you cant back out of and your build is fried, you can go back to how it was ;-)

---

### Post by murdockpt on 2011-11-04
> **haqking said:**
> Tip for the future, after a base install take a clone image of it if it is working using clonezilla or similar.

I take base images, driver update images and complete customised images.

I can drop back to anything i had in about 10 minutes at anytime i like.

So when you customise or add something you cant back out of and your build is fried, you can go back to how it was ;-)

yeah, i fully plan on it. im in class at the monet, but ill post what i see when i get home in about 20 minutes.

---

### Post by murdockpt on 2011-11-04
oh daaaaaaaamn

i have a sneaking suspicion that doing the "delete the partitions, quit the installer, reboot and check again" process doesnt actually delete the partitions, but in case it did...

the partitions are still there after reboot.

what now?

---

### Post by murdockpt on 2011-11-04
CORRECTION: Partitions are deleting and all that jazz. I really dont know whats up.

---

