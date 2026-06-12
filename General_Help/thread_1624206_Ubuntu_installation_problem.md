---
title: "Ubuntu installation problem"
date: 2010-11-17
forum: General Help
---

### Post by Xplat on 2010-11-17
I have always had trouble installing Ubuntu on my Acer Aspire M3641 system. For some reason, even though my computer supports acpi, I have to turn it off in the configuration menu of 9.04 to get it to install.

Because I don't get an error when I try to install it with acpi support, I can't say exactly what the problem is. If I try it on any Ubuntu distro with acpi support on, it takes a long time to load and then shuts the display off. I have to reset afterwards.

To make things worse, I have to install with Ubuntu 9.04 to get it to install because in 9.10 and up there is no pre-installation configuration menu. Then I have to slowly upgrade to the latest version, which takes about 2-3 days right now.

Does anyone know how to fix this?

:confused:

---

### Post by Xplat on 2010-11-17
Bump

I really need help here, I'm switching from Windows to Ubuntu.

---

### Post by blueridgedog on 2010-11-17
Can you turn acpi off in the bios?

Can you try installing using the alternate CD?

---

### Post by Xplat on 2010-11-17
Yes and no.

When I turn acpi off in the bios, it says it can't find acpi, so it won't run.

I haven't tried using the minimal CD, but I don't want to because it doesn't have every feature that the main one does, and because it isn't GUI, I would have to install it differently. I don't know how it would work out, and I don't want to mess up my other files.

---

### Post by blueridgedog on 2010-11-18
The alternate text based install CD is the same Ubuntu, just with a text based installation.  It may solve your installation issues.

---

### Post by Xplat on 2010-11-18
> **blueridgedog said:**
> The alternate text based install CD is the same Ubuntu, just with a text based installation.  It may solve your installation issues.

I suppose that works, I just installed Ubuntu 10.10 on my computer.

I still think that should be fixed, though. The graphic install works on my 8 year old and older computers, so why isn't it working on this 2 year old one?

---

### Post by blueridgedog on 2010-11-19
From the website:

Alternate installer details
The text-based alternate installer can be downloaded from a location near you. This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd *or because their computer requires configuration after the installation is complete in order to use the desktop*.

Many newer systems fall into the second category.

---

### Post by Weedsy on 2011-09-18
I know this thread's getting a bit long in the tooth but I too have a problem installing Ubuntu on Acer Aspire...

Acer Aspire M3641
Intel Pentium Dual CPU E2200 @ 2.20GHz
RAM 2.00 GB
Windows Vista Home Basic. Service Pack 2. 32bit os.
ATAPI DVD A  DH16A6S SCSI CdRom Device


OK here goes... I'm new to Ubuntu, though I feel more than a little familiar with the installation process having spent more than 6 hours yesterday trying to install it.

I downloaded Ubuntu iso from the official website and created a CD. I know this was successful because I installed it onto an ageing Sony vaio notebook without incident. This was installed as the only os - replacing windows xp.

I then tried to install Ubunto on my Acer Aspire desktop which is (sadly still) running win vista 32bit. It failed to boot into Ubuntu from the CD. It started to boot and I got the purple screen but then it stopped saying it couldn't find a live file system. At this point it hung - no keystrokes worked and I resorted to a cold restart of the computer.

Much is writ about the initramfs message about the live file system on this forum so I took the advice offered here and created a USB pendrive... same problem. I ran chkdsk as advised by the Ubuntu installation message but to no avail. Needless to say after repeated reboots and attempts I am still without a working system.

Has anybody else had problems with Acer Aspire desktop systems running Vista 32bit? I thought the cd drive may be the problem because it is a dual DVD/CD thing - but I failed to find anything in the BIOS to try changing here, and it doesn't explain the USB(2.0) pendrive problem.

Any suggestions to try before I crawl back under my microsoft windows stone before emerging in another 10 years to try linux again? (I tries Suse linux 10 years ago and swore I'd wait until 'ordinary people' could use linux before trying again).

Help me please cos I really, really want to run Ubuntu on my destop.

---

### Post by Xplat on 2011-12-21
After some on and off working on this problem, I figured out what went wrong and I fixed it so I can use the regular installer without problems, without additional flags.

If it helps anyone still having this problem, the problem can easily be solved by changing a simple setting in the bios.

The setting that needs to be changed is something like "BootOS" or "MainOS"; changing it from "Windows" to "Other" did the trick.

I suspect the main reason why this happened is because it was booting into an operating system that wasn't what it expected, so it booted the OS the wrong way, requiring certain flags to be passed to the bootloader in order for the OS to boot properly.

But I finally did it! I'm now successfully running Ubuntu 10.04 LTS on my computer. :D

---

