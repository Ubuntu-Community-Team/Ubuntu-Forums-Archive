---
title: "alienware X51"
date: 2012-03-03
forum: General Help
---

### Post by Mecasickle on 2012-03-03
Basically the gamers out there are probably aware that the new Alienware X51 is the new REAL DEAL in portable gaming desktop computers.

Apparently after their premature release they really messed up and it has all kind of hardware and software bugs.

The reason of my post is that I know that of the small group of people who you use alienware's, some have a dual-boot system with ubuntu for research purposes (besides gaming). And I can't even install ubuntu with the USB stick ...

The BIOS loads, recognizes 3 options : 
-Try Ubuntu without installing
-Install Ubuntu
-Check for errors in disc.

After I select any option the screen stays black as if it were to load forever and nothing happens...

Is this a problem of the BIOS (A02) ?? Problem of the motherboard? I received a notice that the Alienware X51 uses a 512e Advanced Format Hard Drive, maybe there is an issue with that?

Of those who have an alienware X51 please let me know if you guys had any success with installing ubuntu on this machine.

Thanks!

---

### Post by Mecasickle on 2012-03-03
*Correction , the Alienware X51 uses a 512 bytes regular hard drive. I'm guessing it has to do with the BIOS?

---

### Post by ronjouch on 2012-03-04
Which version of Ubuntu did you use? Trying [12.04 beta1]("http://www.ubuntu.com/testing/precise/beta1") might be a good idea.

Also, dell support isn't very encouraging (see [this thread]("http://en.community.dell.com/owners-club/alienware/f/3746/p/19439316/20064361.aspx")):
[INDENT]*All we offer on the X51 is Windows 7 Home Premium SP1 (64 bit) support and drivers. I have no idea if you can even find the chipset and component drivers for Ubuntu Linux. These guys on the Linux Forum might offer insights.*[/INDENT]

---

### Post by Mecasickle on 2012-03-04
wow, I tried the new install with 12.04 and it installed, and even aprtitioned the disk. But either way, once it starts booting into ubuntu the screen freezes and nothing can be done. 

My question to this is, what is the root of this problem? Is alienware using some sort of new tech that linux distributions won't run ? 

I mean not even using wubi, and installing ubuntu from windows works. How is this possible? I've had past experiences with my Alienware m11x, but I least I could get the initial splash screen that guided me through the linux installation process

---

### Post by ronjouch on 2012-03-05
> **Mecasickle said:**
> wow, I tried the new install with 12.04 and it installed, and even aprtitioned the disk. But either way, once it starts booting into ubuntu the screen freezes and nothing can be done.
So you confirm that you could use the installer? Did you use "Try Ubuntu without installing" then click on Install Ubuntu on the Desktop, or did you directly "Install Ubuntu"? If you were able to use the live session ("Try Ubuntu without installing"), did it behave as expected?

> **Mecasickle said:**
> My question to this is, what is the root of this problem? Is alienware using some sort of new tech that linux distributions won't run ?
That's possible, yes. If you have some time, you should talk to the kernel gurus, they will have questions for you and will request feedback that will be helpful to the whole community. Give them a shout [on IRC]("https://wiki.ubuntu.com/Kernel/FAQ#Kernel.2BAC8-FAQ.2BAC8-GeneralFindingTeam.How_do_I_find_the_kernel_team.3F") :)

---

### Post by drbcladd on 2012-03-05
Interestingly: I just upgraded to 12.04b on an Alienware 17m. 

Upgrade seems to run flawlessly. Reboot to a kernel panic. Boot recovery laughs as it panics, too.

Download and burn CD of 12.04 daily to see if I can easily boot to it and look into fixing the code (I can boot the other spindle with 11.10 and still read drive 0 so nothing too bad happened). Same kernel panic (or one at a similar point in the boot sequence). 

squashfs seems to pagefault, then die with a null RIP and then the bad stuff comes.

May wonder over to IRC to see if I can be of any help. Probably not but this is why I run beta software.

---

### Post by Mecasickle on 2012-03-05
Ive noticed that it can boot to the install option menu when I switch my booting options from UEFI to Legacy ... But then again even when I see how linux installs itself, I get a LSOD (Linux screen of death) (ill make that up haha) meaning that I get a dark purple color screen with no words or message and it just freezes there.

I've also noticed that apparently the 12.04 Beta files don't have a wubi.exe file inside. Maybe this has something to do with it? Yesterday I even tried installing linux over all the 1Tb of my alienware X51, without any booting success. *sign for me, I had to reinstall Windows all over again.

Here are some Boot Options I have from the initial BIOS splash screen:

Boot Mode: UEFI / Legacy.
Note : 12.04b is detected by both but after installation it can't boot succesfully. Linux GUI seems to be disabled throughout the entire installation process.

CPU Configuration:
 HyperThreading Technology [Enabled]
 XD Bit Capability [Disabled]
 Intel(R) SpeedStep Technology [Enabled]
 Intel(r) C-State Tech [Enabled]

Integrated Devices
 Launch PXE OpROM [Enabled]

I'd appreciate any more thoughts! I think it would be really cool if they make the 12.04 compatible with whatever issue it has with the X51, I honestly don't know if this problem might also be faced by other intel motherbords and/or BIOS.

---

### Post by drbcladd on 2012-03-06
Mecasickle: Have you tried today's (2012-03-06) updates? The kernel updates get past the crash I was having last night. Still not sure what the problem was (looked at the bugs fixed and failed to match one with my symptoms). 

Now I have a graphics problem with X not recognizing the mouse. Not a big problem but I can't rebuild the drivers because the silly headers are a version behind the kernel that was installed. Oh, well.

Hope it gets better soon.

---

### Post by Mecasickle on 2012-03-06
I'm downloading it right now. I'll just have to hope for the best! It's nice to have someone in the Alienware and Ubuntu community as well! (I think we should start our own website haha for the pps out there!)

I also tried installing Linux Mint. By the way, could you check up for me if your m17 has a BIOS switching option between Legacy and UEFI ?

*[EDIT]* Just tried, no luck at all with 12.04b release. It's as if once the wubi.exe file is there I can't boot anymore... really weird

---

### Post by Mecasickle on 2012-03-06
Finally gotting working. I'll be posting the solution / workaround in a while!

---

### Post by Mecasickle on 2012-03-07
I'm developing this website for people who use Ubuntu Linux on an Alienware computer:

[http://quantumbeach.wikidot.com/](http://quantumbeach.wikidot.com/)

It's still in development but the workaround is posted =D

---

### Post by flipper T on 2012-03-07
most convoluted advert for a user´s website i have seen so far...

congrats

---

### Post by will824 on 2012-12-07
Mecasickle thanks for the great work!.

We also created an upgrade wiki for x51 owners who want to improve their machines. Please feel free to contribute and also link it to your great Linux for Alienware forum!:
[http://alienware-x51.wikia.com/wiki/Alienware_x51_Wiki](http://alienware-x51.wikia.com/wiki/Alienware_x51_Wiki)

Thanks!

---

