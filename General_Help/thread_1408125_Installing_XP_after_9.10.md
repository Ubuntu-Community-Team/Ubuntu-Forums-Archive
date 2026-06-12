---
title: "Installing XP after 9.10"
date: 2010-02-16
forum: General Help
---

### Post by bpm07 on 2010-02-16
Hi,  

(First time poster, so apologies if this is in the wrong forum!)

I recently made the transition from Windows to Ubuntu on a rather old laptop, and I'm loving it!  

However, a couple of Windows programs that I need do not run well in Wine (or not at all) so I want to reinstall XP (I have the installation disk) on a small NTFS partition, while keeping Ubuntu intact.  

I came across this thread: [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) and followed the algorithm. XP does the first part of the setup before needing to reboot. After the reboot, the setup will not continue. 

I've followed directions to reinstall grub 2 and also ran grub-mkconfig so now I have the option to boot Ubuntu or Windows. Ubuntu boot works fine, but Windows will not boot, and hence will not continue the installation. 

Has anyone tried this with success, and if so, any good advice?

Thanks in advance for the help! :D

---

### Post by Richard1979 on 2010-02-16
If you don't need 3D games, maybe try installing Windows in VirtualBox inside Ubuntu?

---

### Post by SeaJayEmm on 2010-02-16
It is extremely difficult to Install XP after Ubuntu is installed. It is much easier and less of a headache to go ahead and back up whatever you wish in your ubuntu setup. Pop in the XP disc, format the hdd and install XP. Then install Ubuntu. You will then have dual boot.

---

### Post by bpm07 on 2010-02-16
I've heard that doing so can be quite resource heavy, and as I have an older system (1.6Ghz, 1GB ram) I thought this wouldn't be the way to go...

Would you say that that is folly, and that Windows in Virtual Box will work fine?

---

### Post by hathiphnath on 2010-02-16
> **Richard1979 said:**
> If you don't need 3D games, maybe try installing Windows in VirtualBox inside Ubuntu?

That's a neat idea indeed. If you have at least 2GB of RAM you should definitely consider VirtualBox. Heck, you should definitely give it a try as VirtualBox is free for personal use. With 1GB it's a stretch, but with 2 you should be good. Having no reboots necessary is a blessing. I tried many linux distributions under VirtualBox and it's not hard to use at all.

The hardest part to me was that I somehow assumed that the *guest additions* need to be installed to the host OS, but once I figured out that it was the VB OS that needed those it was a breeze. :)

*Edit:* Ah, you indeed have 1GB. Get the extra 1GB, man. Having no reboots is worth it. I did most my VirtualBoxing under 1,83GHz laptop (one of the early 2-cores) and going from 1GB to 2GB really helped.

Do you have DDR or DDR2? DDR can be quite expensive nowadays.

---

### Post by nerdtron on 2010-02-16
> **bpm07 said:**
> Hi,  

(First time poster, so apologies if this is in the wrong forum!)

I recently made the transition from Windows to Ubuntu on a rather old laptop, and I'm loving it!  

However, a couple of Windows programs that I need do not run well in Wine (or not at all) so I want to reinstall XP (I have the installation disk) on a small NTFS partition, while keeping Ubuntu intact.  

I came across this thread: [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999) and followed the algorithm. XP does the first part of the setup before needing to reboot. After the reboot, the setup will not continue. 

I've followed directions to reinstall grub 2 and also ran grub-mkconfig so now I have the option to boot Ubuntu or Windows. Ubuntu boot works fine, but Windows will not boot, and hence will not continue the installation. 

Has anyone tried this with success, and if so, any good advice?

Thanks in advance for the help! :D

Yes installing XP in Virtual Box is a good idea. However if you're  laptop is a bit old it may have enough resources to run a virtual  machine smoothly.
BTW the link you provided is for Win7. The installation for 7 and XP are different. 
I'm assuming you have another partition to install XP so boot from CD and install it just like a fresh install. be careful not to install it on the Ubuntu partition. It will over write the MBR and you won't be able to boot Ubuntu. To fix this you need to reinstall GRUB via Live CD. You might find this link helpful: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by coldraven on 2010-02-16
You should read this first. To check if your CPU supports hardware virtualisation.


[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

Sometimes it has to be enabled in your BIOS

---

### Post by bpm07 on 2010-02-16
> **coldraven said:**
> You should read this first. To check if your CPU supports hardware virtualisation.


[https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation)

Sometimes it has to be enabled in your BIOS

I ran the command 

```
egrep '(vmx|svm)' --color=always /proc/cpuinfo
``` and it returned nothing, apparently indicating that my CPU does not support hardware virtualization. 

Does this then mean that Virtualbox will also not work? (I only ask because the guide seemed to refer to KVM)

---

### Post by bpm07 on 2010-02-17
I retried the XP installation tonight, only this time I made the Windows installation reformat its partition (leaving the Ubuntu partitions untouched). It worked, Grub is fixed and things work smoothly on both sides. 

Thanks for all the helpful comments!

---

