---
title: "VirtualBox VM considerations"
date: 2010-01-09
forum: General Help
---

### Post by Hedon James on 2010-01-09
Not sure if this is in the correct forum, so please accept my apologies and move to appropriate area if that is the case.  Anyways, on to my question(s)...

Hello everyone,

Quite a lengthy post, but I’ve recently installed Ubuntu Linux on my computer and am attempting to completely migrate away from Windows programs.  I’ve run into some problems with that idealistic concept, realizing that WINE and CrossOver don’t run my Win programs the way they should; no problems…I’ve also recently learned about the wonders of Virtual Machine software.  But now I have numerous questions and concerns about various options using a WinXP Virtual Machine as a guest OS in my Ubuntu Linux host.  I’ve cruised numerous forums and gathered all kinds of information, but I just can’t find the answers to MY specific questions…so I’m asking you folks already “in the know” with VM experience.

In order to make recommendations, I think it’s important you know that the SOLE reason for wanting to do a VM is to run specific Windows programs in Linux that I just can’t replace with Linux programs.  These programs are Quickbooks Pro, Microsoft Zune, and WinTOTAL (real estate appraisal software).  Also, don’t know if this matters, but after much consideration and research, I’ve decided to use VirtualBox OSE as my VM program.

Other important considerations are that I have WinXP (OEM installed) and Ubuntu dual-booting on my 40GB desktop; Win occupies a 29GB partition (although only 21GB is used) and Ubuntu occupies the remaining 11GB.  With that background, I’m having trouble deciding what is the appropriate strategy to implement a VM.  It appears that my primary options are as follows, with questions/concerns for each option discussed below:

1.      Install WinXP as guest OS VM from a “raw” or “native” partition;
2.      Install WinXP as guest from Clonezilla iso image;
3.      Install WinXP as guest from self-created slipstream disk;

Potential considerations for option #1 are that I will not be able to expand my Linux partition, as needs dictate.  Also, if I have a WinXP VM, there’s no reason to continue with a dual-boot arrangement.  I’d like to just wipe out my Win partition and utilize the whole hard drive for Linux.  Option #1 will preclude this in the future.  Also, does this option allow for access to the aforementioned previously installed Win programs on that partition, or does it only create a WinXP environment, with my desired programs to be added from within the VM?

Potential considerations for option #2 are that a cloned image will also be 29GB.  How does this work when the “native” install is 29GB and the Linux install is 11GB?  Seems like the hard drive is completely spoken for, right?  Also considering #1 issues, this seems like a chicken & egg proposition where I need a WinXP VM to wipe out the native partition, but I need the native partition to create and verify the VM.  Is it possible to save the cloned disk image ISO file on an external network drive and have VirtualBox access that image to create my VM, thereby proving its viability before I wipe out the windows partition?  And again, will the cloned image include the aforementioned previously installed Win programs on that partition, or does it only create a WinXP environment, with programs to be added from within the VM?

Lastly, potential considerations for option #3 primarily revolve around the creation of a slipstream disk from Dell OEM-installed WinXP.  My current XP configuration is up-to-date with SP2 and SP3, as well as all the latest hotfixes.  Obviously, this disk will be bare-bones WinXP installation as VM, without anything but XP programs, which isn’t necessarily a bad thing.  Obviously, I will have to install my previously aforementioned WinXP programs in the newly created VM; but this begs the question of “should I just create a basic slipstream install disk, updating SP2 and SP3 from within the VM; or should I try to create a slipstream disk with all SPs and hotfixes that will not require updating?”  Not sure of the pros and cons of each method…any insights from someone who has already done it?

In summary, I think I’ve considered all the potential scenarios, but cannot quantify the risks/rewards of each scenario.  I’m a 2 month old Linux “newbie” and I’d really appreciate some guidance from someone who has already “been there and done that”…  What is the BEST way, in your opinion, to accomplish my stated goals?  Thank you in advance for any insights/guidance you can offer!

---

### Post by mk1w86 on 2010-01-09
I would choose your option 3.  It will probably not make much difference whether you slipstream the SP's and updates or not.  I use slipstreamed installation disks but only so overall Windows installation is quicker.  If this is just a one off install it might be easier to install SP's after XP installation.  One concern is that because you are installing from a Dell OEM disk you might have activation problems because you are not installing directly on Dell hardware and I assume that it is just XP as you say and does not contain loads of Dell crapware.

When you have installed XP in your VM you should install the VirtualBox guest additions (drivers for the virtual hardware and allow mouse pointer integration etc.) by going to Devices>>Install Guest Additions... or by pressing Host+D.

Also I am sure you know from your research that the OSE of VirtualBox does not have USB support.  If you want USB support you will have to use the closed source edition.  You can download it from here:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by Hedon James on 2010-01-11
> **mk1w86 said:**
> I would choose your option 3.  It will probably not make much difference whether you slipstream the SP's and updates or not.  I use slipstreamed installation disks but only so overall Windows installation is quicker.  If this is just a one off install it might be easier to install SP's after XP installation.  One concern is that because you are installing from a Dell OEM disk you might have activation problems because you are not installing directly on Dell hardware and I assume that it is just XP as you say and does not contain loads of Dell crapware.

When you have installed XP in your VM you should install the VirtualBox guest additions (drivers for the virtual hardware and allow mouse pointer integration etc.) by going to Devices>>Install Guest Additions... or by pressing Host+D.

Also I am sure you know from your research that the OSE of VirtualBox does not have USB support.  If you want USB support you will have to use the closed source edition.  You can download it from here:

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Ohhhh...good call on the OSE version.  I read that, but it didn't register.  Inasmuch as I plan to save data from Windows program on an external USB HDD, this would've been a HUGE headache later on, but an easy download and replace today.  I'm sure you saved me a fair amount of frustration before I figured it out...THANK YOU!!!

Thanks for the other comments also; I was already leaning that way, but looking for confirmation and the details you suggested.

Anyone else have thoughts, before I implement MK's comments?

---

### Post by mister_playboy on 2010-01-12
How much RAM do you have and what kind of processor in your computer?  If you only have a 40GB harddrive, that implies your computer is quite old... trying to run XP on top of Ubuntu may be beyond your capabilities.

1.25GB total of RAM is about the lowest amount acceptable for what you want to do and have things remain responsive.  If you have less than that you'll be better off dual booting.

---

### Post by Hedon James on 2010-01-12
> **mister_playboy said:**
> How much RAM do you have and what kind of processor in your computer?  If you only have a 40GB harddrive, that implies your computer is quite old... trying to run XP on top of Ubuntu may be beyond your capabilities.

1.25GB total of RAM is about the lowest amount acceptable for what you want to do and have things remain responsive.  If you have less than that you'll be better off dual booting.

You are correct that the computer is quite old...about 7 years old.  But the processor is actually quite fast, being a dual core 2.4 GHz in a Dell Dimension, and I bumped up the RAM to 1.5GB at purchase.  Does that change your prognosis at all?

---

### Post by mkvnmtr on 2010-01-12
It only takes me about 512Mb to run Ubuntu well but if I was going to run a windows  in a virtual box I would add another gig of ram to your system. It will make every thing easier. I would recomend that you start with some quick and easy distros for practice. It has been the little things that have ruined my installations but they are so easy to redo that I just delete and redo. I quit using disks and use an ISO image and in no time I have it up and running. Do 3 or 4 and your windows will be much smoother. I put off trying for a couple of years because I thought it would be complicated but it is not.The thing when you are setting up it is nothing to do it again.

---

