---
title: "BIOS? bootloader? hardware problem?"
date: 2012-09-25
forum: General Help
---

### Post by NokoNHK on 2012-09-25
Specs:
 AMD A4-3400 2.70 GHz
 4GB DDR3 SDRAM
 1TB HDD
 Windows 7 Home Premium 64 bit (read below for current status)
 220 W power supply
 BIOS version P01.A0
 

 and here is a link to more detailed specs:
 [http://us.acer.com/ac/en/US/content/model/PT.SHFP2.003](http://us.acer.com/ac/en/US/content/model/PT.SHFP2.003)
 

 Here is my problem, I have a fairly new computer (3 months old) that has been doing great until a couple of weeks ago. It would lock-up during any task with the Windows 7 OS it came with. Programs would not respond for 3-20 seconds but I could move my mouse, system processes would NOT go up and RAM usage was normal during lock-ups too. Updating drivers, scanning for viruses, checking registry errors and updating my computer through acer alleviated the problem, but did not solve it, making me think it is a software issue and not hardware. I ran memtest, hard drive health and other hardware tests to make sure though and all passed saying hardware was good. I then put ubuntu 12.04 on the computer and the problem is still there.  I start to assume it could be a BIOS problem and download (through the Windows 7 OS) the correct BIOS version for my motherboard off of the ACER website. I then run one last sweep of driver updates (audio, mouse and keyboard) and restart *before* flashing my BIOS. The computer starts hanging on the boot loader screen where I choose Ubuntu or Windows 7, with different error messages each time, “out of disk; grub recovery”, blank screen, and a windows STOP blue screen. I can only assume I have messed up my bios without knowing and go in to the BIOS menu before the computer boots and am still running P01.A0, the same version I was running before I downloaded the new BIOS version, P01.A4. I am very confused now, as I can't get a grip on what the problem exactly is. I get a fresh Ubuntu 12.04 64 bit disc and a fresh Windows XP 64 bit disc and am unable to put either on my computer. I try to wipe my HDD clean but only manage to get Windows 7 off and not Ubuntu.
 

 Strangest thing is, out of every 10 times or so I turn it on, it can get past boot and fully run Ubuntu (while still doing the lock up) but now I think I have messed something up, either to do with the boot loader or the BIOS.
 

 Anyone have any ideas? Turning the computer off runs the risk of not being able to boot again, but I really want to fix this, or find out if this is a hardware problem. Any help or thoughts would be appreciated!

---

### Post by Bashing-om on 2012-09-25
NokoNHK; Hi ! Welcome to the forum.

As this computer is fairly new, UEFI may be a factor.
read these links for the info:
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)

another thought: Large drive installs, see this thread.
[http://ubuntuforums.org/showthread.php?p=12254717#post12254717](http://ubuntuforums.org/showthread.php?p=12254717#post12254717)



additional "advise":
 1. reset your bios to factory defaults . read your documentation on how, some you can pull the mb's battery, some can jumper cmos pins.
 2. in bios set the cd as 1st boot priority and boot up the ubuntu install disk.
 3. run ubuntu in "try ubuntu" mode and see how your system then performs.[INDENT]best of luck to ya ..we are here for support <==BDQ

[/INDENT]

---

### Post by NokoNHK on 2012-09-25
I had to use a similar workaround to get Ubuntu installed on my computer like in your 2nd link. I am unable to run the live cd on try ubuntu mode. I can't get back onto the ubuntu on the HD now. writing this from my phone haha. ubuntu cd goes into grub rescue sometimes and sometimes it says "no prefix set".  thanks for your help, at least i have a grasp on what might be the problem now.

---

### Post by Bashing-om on 2012-09-26
the "no prefix set" is fixable.
see:[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
and follow the trail.

Problem being ya going to have to boot up the live cd... we work on that one.
At one time you booted up "nomodeset" what haps now ?

[INDENT]try'n to help <== BDQ

[/INDENT]

---

### Post by NokoNHK on 2012-09-26
i don't think i have seen "nomodeset" before. i get to a purple screen on the live CD and then then it goes blank and my monitor goes the sleep while the HD and fan spin.


UPDATE:

i am able to get to a black and white booter that says try ubuntu, install, and check disc for defects. all three lead to my screen going blank and unresponsive. near the bottom it says i can edit commands before booting or open a command-line. can i use these to my advantage?

---

### Post by cariboo on 2012-09-26
> **NokoNHK said:**
> i don't think i have seen "nomodeset" before. i get to a purple screen on the live CD and then then it goes blank and my monitor goes the sleep while the HD and fan spin.


UPDATE:

i am able to get to a black and white booter that says try ubuntu, install, and check disc for defects. all three lead to my screen going blank and unresponsive. near the bottom it says i can edit commands before booting or open a command-line. can i use these to my advantage?

When you are at this screen, press F6 and us the arrow keys to navigate to nomodeset, us the space bar to select it, then press ESC and then press enter. you should be taken to the Live CD desktop.

Nomodeset has been around for at least the last 4 release, before that it was called Safe Graphics Mode.

---

### Post by NokoNHK on 2012-09-26
the boot screen didn't seem to respond to F6, but somehow the live cd booted anyway! i am now in the normal 12.04 live CD, glimmer of hope.

UPDATE:

I formatted the HDD and am still unable to install either ubuntu or windows. I am however, able to run the live CD about every 3 times I try (better than it was! haha).  I'm thinking that if I'm starting with a fresh HDD and I'm unable to load any OS on to it, it has to be a hardware or bios problem, I'm not sure if it can be anything else.  next paycheck I plan to buy a SSD and install the OS's on it and see if that works, if it does I can confirm it's the HDD. For right now, the computer is running on the live CD and I have yet to see it do the locking up that I described in my first post (although we shall see with more use). This makes me assume it's a HDD problem even more but still not confident.

---

