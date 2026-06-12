---
title: "Boot problems"
date: 2012-01-03
forum: General Help
---

### Post by Urie on 2012-01-03
Ok i have searched everywhere and i can only find help for windows, or some that isnt relevant

Im not sure if this is a hardware or OS problem, When i boot i get nothing a black screen with a flashing white line on the top right of the screen (even if use a live CD)

I can get into the bios and i checked the event log, there was a problem with the CMOS Battery so i replace that. But it still wont boot.

Chris

---

### Post by MG&amp;TL on 2012-01-03
...still won't boot?

How?

What does the event log say this time?

---

### Post by Urie on 2012-01-03
The last thing in the event log is that it was cleared, (Which i did casue it was full of wrong dates and the same errors about the CMOS battery)

---

### Post by MG&amp;TL on 2012-01-03
okay, so how does it not boot?

same blinking prompt?

Can you try holding shift a little while before the end of the BIOS screen, this should bring up GRUB-if it doesn't it's not booting the OS.

Are there any system beeps, etc?

---

### Post by Urie on 2012-01-03
Ok i didnt get the Grub Menu, but even if i boot from a live cd i get a blank screen with a white line (courser) in the top left then after about 5-10 mins i get the Ubuntu loading screen (i have never seen it take that long) then it just does nothing, just shows the loading screen.

---

### Post by Urie on 2012-01-03
ok so this gets weirder and weirder i tried a linux Mint live disk and got this

---

### Post by drklunk on 2012-01-03
> **Urie said:**
> ok so this gets weirder and weirder i tried a linux Mint live disk and got this

if it were possible Id save that as my wallpaper.

have you tried formatting your hard disk, or partition, from bios? this is the only solution I can think of that would solve the problem for sure

---

### Post by Urie on 2012-01-03
There is no option for disk formatting and partitions in my bios

---

### Post by MG&amp;TL on 2012-01-03
Very odd. Does your computer manufacturer provide hardware support?

---

### Post by Urie on 2012-01-03
Not that i know of, if it helps its a Dell GX series

---

### Post by drklunk on 2012-01-03
could it be your optical drive? did the issue start while trying to change your OS or did it just start doing this when you tried to turn it on one day?

if its possible I would try booting from a thumb drive, see how that goes

---

### Post by xc3RnbFO8P on 2012-01-03
Read this how to get in to grub menu:
[http://ubuntuforums.org/showthread.php?t=1613132]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by topsites on 2012-01-03
First things first.

As a general rule, if you are booting from something other than what the PC is used to booting from (such as the HDD) it is quite possible that you need to manually edit the Boot ORDER inside your BIOS, ALWAYS make the media from which you intend to Boot FIRST in line.

Otherwise it could try and boot from something that won't boot, and hang in the process.
And if it still gives you trouble, at least we've eliminated this possibility.

So for example if I want to boot via Live CD, I go into my BIOS and configure in order of boot:  1. CD-Rom (then 2 and 3 can be interchangeably USB stick / HDD) conversely if I wanted to boot from HDD I would make that 1. HDD and then whichever for 2 and 3 and so on.

Always make your bootable media (the one you intend to use on next boot) FIRST in line.

---

### Post by Urie on 2012-01-03
Ok thanks ill give that a go and ill try booting from a USB thumb drive

---

### Post by Bobhuber on 2012-01-03
IMHO - Bad Memory stick - Or video memory

---

### Post by oldfred on 2012-01-03
What video card? nomodeset works for many, and I have to use it for my nVidia.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

---

