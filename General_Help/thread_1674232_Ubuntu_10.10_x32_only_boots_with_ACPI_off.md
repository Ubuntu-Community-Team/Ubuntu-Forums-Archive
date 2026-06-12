---
title: "Ubuntu 10.10 x32 only boots with ACPI off"
date: 2011-01-23
forum: General Help
---

### Post by BigRicky on 2011-01-23
Hey, all,

Just installed Ubuntu 10.10 32 bit on my new Dell laptop. The computer's specs are: 

Processor: AMD Athlon II P340 Dual-Core Processor 
Memory: 3.00 GB 
Graphics: ATI Mobility Radeon HD 4250 

The only way I can get the thing to boot is with the parameter acpi=off.  This being a laptop, not having access to battery information is quite annoying.  If I try and boot without it, after I make my GRUB selection it simply shows a blinking "_".   

Anyone have any ideas?

Many thanks,
Ricky

---

### Post by Hippytaff on 2011-01-23
Are there graphics drivers to install...boot with ACPI off and then got to System -> Administration -> Additional drivers to see if there are any graphics ATI drivers to install

---

### Post by BigRicky on 2011-01-23
Hey, Hippytaff, thank you for your quick reply.  I did install the proprietary ATI driver, but this did not make a difference.

Ricky

---

### Post by Hippytaff on 2011-01-23
does the driver appear when you do 
```

lsmod

```

---

### Post by BigRicky on 2011-01-23
It's 'fglxr' that I am looking for, correct?  Yes, it is there.

---

### Post by Hippytaff on 2011-01-23
and you've rebooted since installing it (obviously you have to discover that it's not working)

Maybe try uninstalling and reinstalling it!?

---

### Post by BigRicky on 2011-01-23
> **Hippytaff said:**
> and you've rebooted since installing it (obviously you have to discover that it's not working)
Yes.
> **Hippytaff said:**
> 
Maybe try uninstalling and reinstalling it!?

The driver or the OS?  This is my third install of Ubuntu.  I installed Ubuntu 10.10 64 bit via CD and had the same problem, then redownloaded it and verified the MD5 and installed via USB.  I saw an Ubuntu User magazine for sale that came with Ubuntu 10.10 32 bit, so I bought it and gave it a whirl.  This is why I am running the 32 bit OS.  This is the first install where I've installed the graphics driver, though.

I am confused on one thing, though.  This ACPI is a power management thingymabobber, yeh?  So how does a graphics driver influence whether or not I can use ACPI?

---

### Post by Hippytaff on 2011-01-23
I meant reinstall the driver and good question...I'm afraid I'm fairly new to this too. The usual procedure is to choose to install proprietery drivers etc when you install the ubuntu, then these kind of things don't tend to crop up, but I really don't understand why the driver doesn't seem to be working :?

---

### Post by BigRicky on 2011-01-23
So after reinstalling the driver in Ubuntu, it asks to reboot to finish the installation.  This time around, however, I noticed that the installation wasn't completing because it would just hang and wouldn't boot up.  My 'acpi=off' parameter didn't hold up over reboots and must be manually entered each boot.  So I found out which file to edit so that this parameter can last, and it turns out it's the etc/default/grub file.  I tried editing it through the GUI (where I and most other twenty-year-olds are most comfortable) but I didn't have permission.  So I messed around in terminal until I found out what I needed to do was sudo vi.  Great.  All I know about vi is that it's some old programming interface that has probably been mostly used to write FORTRAN and some other archaic languages and that it's what my dad (a programmer at HP) uses because he is also old.  

None-the-less I used vi to edit the GRUB file and successfully appended the parameters.  (Which gave me a great sense of accomplishment.)  I rebooted it and it loaded right up- I didn't have to manually specify the parameters!  Yay!  So I reinstalled the graphics driver, rebooted my machine, so the graphics driver should be fully installed now, yeh?  Took out the parameter in vi, rebooted and got nothing.  Still doesn't work.  =(

So I really haven't the foggiest what to do now.  I am most grateful for your assistance, though.

---

### Post by Hippytaff on 2011-01-23
wow...your far more accomplished than me...I only use vi to edit the sudoers file and that's because I have to visudo...I tend to use nano...anyway it's very odd, and maybe there is a bug...did you check the[ launchpad bug site]("https://bugs.launchpad.net/")

I know linux has diffuclties with ati and Nvidia but these are fairly ironed out recently. Sounds like your dad would be better placed than me to help you out ;-)

---

### Post by BigRicky on 2011-01-23
I swear I'm not accomplished in the ways of vi at all!  I had to look up the commands to use the darn thing, which it turns out aren't anywhere near intuitive.  Thanks for the site reference; I looked in there but didn't find anything.  

As to my dad, I once asked him if he knew much about Ubuntu when I was having some problem or other, and he asked what that was.  When I told him it was the most popular distribution of Linux he asked if I was certain, because he had never heard of it and he thought that Red Hat was.  Like I said, he's old.  =P

Something just came to mind, though.  I am in the US Air Force and stationed in England, and one of the attractions I had to buying this laptop here at the base exchange rather than buying one from back home for cheaper and having it shipped over was that this computer was advertised as "dual voltage."  I thought that meant that it would come with two cables, one for the stateside-like prongs and one for the odd ones these chaps around here use for some reason.  Alas, however, it only came with the US plug.  Perhaps there's some sort of BIOS difference?  Wouldn't that explain why a power management utility would go haywire?  I'll try flashing the BIOS tomorrow evening, but it's nearly midnight here and I'm getting up at 0530 tomorrow, so evening, gents!

---

### Post by BigRicky on 2011-01-23
Sorry about the double post, the internet here in the dorms is complete ****.  Turns out Javelin Broadband is bullocks, at least here.  =/

---

### Post by BigRicky on 2011-01-24
So I flashed my BIOS, which it turns out is much more difficult to do in Linux than Windows.  (Used FreeDOS and Startup Disk Creator)  

No effect.  =(

I was messing around in my BIOS and it says it's compatible with ACPI, which seems quite understandable considering this is a new laptop and a not an ancient one.  Anyone have any inkling as to why Ubuntu works only with ACPI disabled?  

I *really* appreciate any input anyone can provide, even if it's just a hunch.  

Many thanks,
Ricky

---

### Post by sanderj on 2011-01-24
Not even a hunch, just a trial-and-error idea: have you tried older and newer versions of Ubuntu? So:

(9.04)
9.10
10.04
11.04 Alpha 1

They have different kernel versions, so that could change the ACPI stuff.

---

### Post by Hippytaff on 2011-01-24
> **sanderj said:**
> Not even a hunch, just a trial-and-error idea: have you tried older and newer versions of Ubuntu? So:

(9.04)
9.10
10.04
11.04 Alpha 1

They have different kernel versions, so that could change the ACPI stuff.

Good point, or you could just try installing older kernels - [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

but it can go wonky, though an excellent learning experience!

---

### Post by davidmohammed on 2011-01-24
acpi=off is quite drastic - have you tried any of the "kernel options" (search for common boot options) in [this]("https://help.ubuntu.com/community/BootOptions") web-page?

---

### Post by BigRicky on 2011-01-26
Hey, gents, thanks for all the replies.  I tinkered around with the different boot parameters on the site provided by davidmohammed, and I found that the parameter 'pci=noacpi' also worked.  I now have a power bar, which is most convenient.  But my sound has disappeared...  Is this coincidence?  I tried looking up what the parameter does but couldn't get  any information other than it has to do with IRQ stuff which doesn't mean anything to me. Am I best off just putting this boot parameter in permanently, or is there a solution that makes it so I don't need it?

Many thanks,
Ricky

---

### Post by davidmohammed on 2011-01-26
some stuff on irqs [here]("https://help.ubuntu.com/community/DebuggingIRQProblems") - it has a few more boot options to try.

Possibly you should have a closer look at what pci cards you have physically in your motherboard - maybe pull/rearrange the cards could help.

---

### Post by IWantFroyo on 2011-01-26
Toshiba T235D S1360. Solved problem with pci=noacpi, and I still have sound and battery icon. I did just use update manager from 10.04, though. If you have sound problems (and no sound configurations are working), try that.

---

### Post by BigRicky on 2011-01-30
Hey, all, 'pci=noacpi' seems to be the magic argument.  As to the sound, my last run in with Ubuntu was Hardy Heron and I believe in that one the sound icon could be individually meddled with, but this one is part of an indicator bar thing.  Anywho, all is well, and I appreciate all your help.

---

### Post by thomi_ch on 2011-03-15
hey all

have made a upgrade from 10.04 to 10.10.. and get the same problem: system stopping, blinking cursor, last line on boot process:
registered taskstats version 1

i now added pci=noacpi to the kernel line:
edit: /etc/default/grub (normally i use vi to edit files like this)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"

then: sudo update-grub
. reboot.. and voilà...

there is also another kernel option, that work "nolapic"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"
this option seems to work better with eg. changing sound up/down over Fn keys..

the system works fine.. all seems ok..

but at the end.. maybe there is a bug on launchpad.. already made a short search, but can't find one..

cheers
thomi

---

### Post by markgw on 2011-04-04
For anyone still suffering from this problem, you might want to try [this solution]("http://ubuntuforums.org/showthread.php?p=10636431#post10636431"), if you're using a machine like the OP on that thread.
Worked for his Toshiba Satellite L670D-102 and my Toshiba Satellite C660-153.

---

### Post by Chitown on 2011-04-25
> **thomi_ch said:**
> hey all

have made a upgrade from 10.04 to 10.10.. and get the same problem: system stopping, blinking cursor, last line on boot process:
registered taskstats version 1

i now added pci=noacpi to the kernel line:
edit: /etc/default/grub (normally i use vi to edit files like this)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"

then: sudo update-grub
. reboot.. and voilà...

there is also another kernel option, that work "nolapic"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nolapic"
this option seems to work better with eg. changing sound up/down over Fn keys..

the system works fine.. all seems ok..

but at the end.. maybe there is a bug on launchpad.. already made a short search, but can't find one..

cheers
thomi

After tying this:  
now added pci=noacpi to the kernel line:
edit: /etc/default/grub (normally i use vi to edit files like this)
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi"

I had to change it to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash noapic acpi=off"

and system was able to boot properly

---

