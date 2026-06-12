---
title: "Ubuntu 11.04 Wubi Problem"
date: 2011-04-29
forum: General Help
---

### Post by eklikeroomys on 2011-04-29
Halo, 

I am unable to install Ubuntu from within Windows. I ran Wubi, restarted, and selected Ubuntu to boot, then it just stops after showing some error codes. 

Has someone had similar problems?
Or maybe some suggestions?

Thank you!

Chris

---

### Post by backles on 2011-04-29
> **eklikeroomys said:**
> Halo, 

I am unable to install Ubuntu from within Windows. I ran Wubi, restarted, and selected Ubuntu to boot, then it just stops after showing some error codes. 

Has someone had similar problems?
Or maybe some suggestions?

Thank you!

Chris


I am able to install it. However it won't boot into ubuntu after the installation. It will only show the error codes too.

Here are my specs

HP ENVY 14
win 7 64bit
4G RAM
i5
internal graphic card with switchable ATI HD 5650

I tried the wubi and the wubi inside the ISO file. None of them work. Please help

---

### Post by bcbc on 2011-04-29
Did you happen to catch what the error was?

Also brand and model and graphics card are good.

For the HP envy there's this [http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/)

---

### Post by backles on 2011-04-29
> **bcbc said:**
> Did you happen to catch what the error was?

Also brand and model and graphics card are good.

For the HP envy there's this [http://linuxenvy.blogspot.com/](http://linuxenvy.blogspot.com/)

That is such a good news that someone is working on ubuntu for HP envy since there's always been issues with my laptop. I couldn't really understand what the error is since I am not a computer science major. But one of the issue with 10.04 or 10.10 is that whenever I boot into ubuntu, I couldn't see anything on the screen. I have to manually turn up the brightness every time. 

However, this time with 11.04, I can't even boot into the OS. After I select ubuntu (windows boot up option), then select ubuntu (ubuntu boot up options), it flash the something error really fast and disappear. It was too fast that I couldn't get any info out of it. After all that, it's all dark. I tried to turn up the brightness, then I found out that there are a lot of code on my screen. It will just sit there, however, I can type code on it too but it wouldn't do anything. I am not so sure if it only happens on HP laptop or every semi-new laptops?

I really wish to use ubuntu without deleting my windows since there are some softwares only working on windows. I was so desperate that I even tried to install it alongside windows but found out I don't have a vacant partition......Hopefully the wubi issue will be solved

---

### Post by bcbc on 2011-04-29
> **backles said:**
> That is such a good news that someone is working on ubuntu for HP envy since there's always been issues with my laptop. I couldn't really understand what the error is since I am not a computer science major. But one of the issue with 10.04 or 10.10 is that whenever I boot into ubuntu, I couldn't see anything on the screen. I have to manually turn up the brightness every time. 

However, this time with 11.04, I can't even boot into the OS. After I select ubuntu (windows boot up option), then select ubuntu (ubuntu boot up options), it flash the something error really fast and disappear. It was too fast that I couldn't get any info out of it. After all that, it's all dark. I tried to turn up the brightness, then I found out that there are a lot of code on my screen. It will just sit there, however, I can type code on it too but it wouldn't do anything. I am not so sure if it only happens on HP laptop or every semi-new laptops?

I really wish to use ubuntu without deleting my windows since there are some softwares only working on windows. I was so desperate that I even tried to install it alongside windows but found out I don't have a vacant partition......Hopefully the wubi issue will be solved
This is unlikely a wubi issue. It's more likely the kernel. I've been reading about backlight issues on some other model recently as well (gateway nv79). The trick is to find out what the kernel boot workaround is (if any) - and if not, find a release that works for you.

If you search bugs.launchpad.net it also turns up some clues e.g. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/755226](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/755226) shows that someone has been able to get natty installed on an Envy (maybe you can ask the poster what they did?)

---

### Post by backles on 2011-04-30
> **bcbc said:**
> This is unlikely a wubi issue. It's more likely the kernel. I've been reading about backlight issues on some other model recently as well (gateway nv79). The trick is to find out what the kernel boot workaround is (if any) - and if not, find a release that works for you.

If you search bugs.launchpad.net it also turns up some clues e.g. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/755226](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/755226) shows that someone has been able to get natty installed on an Envy (maybe you can ask the poster what they did?)

Thanks a lot for the rapid response. Would you tell the kernel more in detail for me? I am a newbie for ubuntu. I've emailed the guy who got the ubuntu installed on his laptop. Hopefully it will work out for me too.

---

### Post by bcbc on 2011-04-30
> **backles said:**
> Thanks a lot for the rapid response. Would you tell the kernel more in detail for me? I am a newbie for ubuntu. I've emailed the guy who got the ubuntu installed on his laptop. Hopefully it will work out for me too.

Here's a pretty decent introduction to kernel boot options: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by backles on 2011-04-30
> **bcbc said:**
> Here's a pretty decent introduction to kernel boot options: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Since you said it's most likely the kernel's problem, does it also mean that even if I install ubuntu with the partition, it wouldn't work either?

---

### Post by bcbc on 2011-04-30
> **backles said:**
> Since you said it's most likely the kernel's problem, does it also mean that even if I install ubuntu with the partition, it wouldn't work either?
Yes. When Wubi does it's install on the first reboot it is actually booting the linux kernel, and then running the standard installer (ubiquity) - so the wubi-specific problems relate more to the virtual disks (e.g. /host/ubuntu/disks/root.disk not found or 'no root file has been defined'). The problems you are seeing is the kernel failures, before ubiquity even starts.

What I suggest is to burn an Ubuntu CD or create a USB, then boot from it in 'Live' mode (Try without installing). You can experiment with boot options, and figure out what it will take to install. Then you can decide whether you want a wubi or a normal install...

---

### Post by backles on 2011-04-30
> **bcbc said:**
> Yes. When Wubi does it's install on the first reboot it is actually booting the linux kernel, and then running the standard installer (ubiquity) - so the wubi-specific problems relate more to the virtual disks (e.g. /host/ubuntu/disks/root.disk not found or 'no root file has been defined'). The problems you are seeing is the kernel failures, before ubiquity even starts.

What I suggest is to burn an Ubuntu CD or create a USB, then boot from it in 'Live' mode (Try without installing). You can experiment with boot options, and figure out what it will take to install. Then you can decide whether you want a wubi or a normal install...

Yeah, I've burned the CD and wished to install ubuntu with its own partition. But HP company is so stupid that they've got 4 primary partitions on my laptop's harddrive.[IMG]http://www.mediafire.com/imgbnc.php/467fe7a2f71fbb183101e5c5d803856d9de694855d3afcc0f8bb37253b6f084e6g.jpg[/IMG]

I don't really want to lose any files on my current windows therefore I am kinda stuck. As long as wubi will work for me, I will be a happy man

---

### Post by t3h_pwnage on 2011-05-16
I would like to say that I own an HP Envy 14 myself and I am running into the same exact issue (the issue being that after the second restart during the installation process the screen is completely black and no buttons work and I have to power off the laptop by holding down the power button for 3 seconds). 

I tried [this]("http://ubuntuforums.org/showthread.php?t=1639198")solution however it did not fix the issue (actually I tried Solutions 1&2 from Problem 2 from that thread and neither of them fixed it).

I will now try [this]("http://ubuntuforums.org/showthread.php?p=8882586#post8882586") solution. I hope it works...

---

### Post by t3h_pwnage on 2011-05-17
Heh, nevermind it did not work. I cannot even get to the command line prompt. I have the same problem as "Taylor Franklin" from the thread I mentioned above.

The guy who said it's a kernel problem is probably right. Something is fundamentally wrong with this install. I will try as a last attempt to install Linux in a separate partition (without having to resort to wubi). I hope it works otherwise no Linux for me :(

P.S. Could the problem be that the Linux I'm installing is 32 bit instead of 64 bit?

---

### Post by t3h_pwnage on 2011-05-17
ROFL WOW GG Linux

I burned a 32-bit Linux 11.04 .iso on a CD and booted from a CD and guess what happened...

...the same crap with the black screen and no command prompt. There is literally *nothing* I can do except raise/lower brightness and power off the computer (by holding the power button down for 3+ seconds). Nothing I type works. Here, I'll attach a picture for you guys to see:

[img]http://ubuntuforums.org/attachment.php?attachmentid=192397&stc=1&d=1305610824[/img]

The unknown key thing is me increasing the brightness. Before that there are a bunch of errors about my radeon graphics card. I would gladly install a Linux driver for it, akin to how [this guy describes it]("http://ubuntuforums.org/showthread.php?p=8882586#post8882586"), but there is no way to get to the command prompt. If someone could write a guide on how to do it from a Live CD I would appreciate it, otherwise I will have to wait until they patch Ubuntu to support my machine.

---

### Post by ishankhare07 on 2011-06-06
i had a bit different problem...
using Wubi i installed ubuntu 11.04 inside my win7 ultimate x86,
on an empty 150Gb partition (i chose installation size 30Gb in the installer)....everything worked well...extracted files etc. thrn i chose to reboot now.
On rebooting i selected ubuntu but i shows an error message like this:
try[hd0,0]wubildr missing...


Asus motherboard,intel core 2 duo,RAM-4GB.

---

### Post by Rubi1200 on 2011-06-06
> **ishankhare07 said:**
> i had a bit different problem...
using Wubi i installed ubuntu 11.04 inside my win7 ultimate x86,
on an empty 150Gb partition (i chose installation size 30Gb in the installer)....everything worked well...extracted files etc. thrn i chose to reboot now.
On rebooting i selected ubuntu but i shows an error message like this:
try[hd0,0]wubildr missing...


Asus motherboard,intel core 2 duo,RAM-4GB.
Hi and welcome to the forums :-)

Please don't hijack other people's threads especially ones that are old. It is not considered good netiquette and makes offering support harder.

You should request to have this moved to a new thread by using the Report Abuse button on the left.

That said, after you see the error does the boot process continue or just stop there?

---

