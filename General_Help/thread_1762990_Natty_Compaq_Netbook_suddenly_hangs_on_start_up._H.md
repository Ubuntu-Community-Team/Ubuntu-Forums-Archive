---
title: "Natty Compaq Netbook suddenly hangs on start up. Help!"
date: 2011-05-19
forum: General Help
---

### Post by feag on 2011-05-19
Hi there

I had no trouble installing Natty from a USB stiick on our brand new Compaq Mini CQ10-61-CA Notebook last week.  I've been loving it!  It's fast and I haven't had any problems until now.

Today I was using Libre Office (?) saved my document, and closed the lid to save the battery.  At the time I had been using a  flash drive that included the Natty install stuff.  When I reopened the computer it to continue working, it appeared frozen.  I gave it a few minutes to catch up, nothing.  I gave it a hard restart.  I didn't think to take the flash drive out, I'm wondering if that led to my problems.

Now when it starts I get the Compaq manufacturer's screen quickly followed by 
GNU GRUB  version 1.99~rci-13ubuntu3
With choice of 
Ubuntu, with Linux 2.6.38-8-generic
Ubuntu, with Linux 2.6.38-8-generic (recovery mode)
Memory Test (memtest86+)
Memory Test (memtest86+ serial console 115200)

Option 1: I get a black screen with a blinking cursor that eventually changes to the familiar purple Ubuntu start up screen.  It hangs here.
Option 2: Lots of information!  Computer quickly runs through start up, then hangs at this point
[4.617432] ata4: DUMMY
[5.108108] ata1: SATA link up 3.0 Gbps (SSatus 123 SControl 300)
[5.109129] ata1.00: ATA-8: ST9250410AS, 0006HPM1, max UDMA/100
[5.109224] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[5.110359] ata1.00: configured for UDMA/100
[5.110726] scsi 0:0:0:0: Direct-Access  ATA ST9250410AS 0006 PQ
: 0 ANSI: 5
[5.111414] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[5.111519] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: 250 GB/232
GiB)
[5.111892] sd 0:0:0:0: [sda] Write Protect is off
[5.112185] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[5.183959] sda: sda1 sda2 < sda5 >
[5.184946] sd 0:0:0:0: [sda] Attached SCSI disk
Begin: Running /scripts/local-premount ... done
[5.440375] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[5.440446] EXT4-fs (sda1): write access will be enabled during recovery
[5.533098] EXT4-fs (sda1): recovery complete
[5.533672] EXT4-fs (sda1): mounted filesystems with ordered data mode. Opts:
(null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.

...and there it stops.  

My husband also tried one of the memory tests but he said it came back with no errors.  He then tried running Ubuntu from the flash drive, no luck.  He tried re-installing ubuntu from the flash drive, also no luck.  Everything we try is slow and then hangs.

Any suggestions would be greatly appreciated!  If you need any more information, please let me know.  Thank you.

---

### Post by zia.newversion on 2011-05-19
You must have done a lot of effort writing all that without the Copy-Paste option. Kudos that.

I see that failsafe mode isn't that failsafe. But it does provide a lot of information, which unfortunately, I am neither qualified enough or competent enough to understand completely. However, from the things that I *can* understand, I think the problem is not with the hardware.

Does the cursor keep blinking after the safe-mode text is displayed? If yes, then perhaps there's something after the /scripts/init-bottom that it needed to execute, but it's not there. If the cursor doesn't appear or is frozen as well, that might mean something's wrong with the kernel, so it can't decide which service to start or something like that.

I don't think memory has to be a problem because 1) memory test came out fine and 2) memory shouldn't get damaged just by closing the lid or a cold-reboot.

I think from the information provided above (and the fact that it's "Mini"), you don't have an optical drive. But then again, maybe it did't probe optical drives right then... So, if you indeed have an optical drive attached, try booting with a CD.

> ... He then tried running Ubuntu from the flash drive, no luck. He tried re-installing ubuntu from the flash drive, also no luck. Everything we try is slow and then hangs.
Also, what exactly do you mean by no-luck? Does it freeze exactly like that? Please enlighten us about the situation with the flash drive. If we can make booting with flash-drive work, perhaps a solution can be found.

---

### Post by feag on 2011-05-19
> **zia.newversion said:**
> Does the cursor keep blinking after the safe-mode text is displayed? If yes, then perhaps there's something after the /scripts/init-bottom that it needed to execute, but it's not there. If the cursor doesn't appear or is frozen as well, that might mean something's wrong with the kernel, so it can't decide which service to start or something like that. Nope, no cursor, nothing.

> **zia.newversion said:**
> I think from the information provided above (and the fact that it's "Mini"), you don't have an optical drive. But then again, maybe it did't probe optical drives right then... So, if you indeed have an optical drive attached, try booting with a CD. No, like you say, it's a mini, we just have USB.  When we boot with the USB we do get as far as the 'Run Ubuntu/Install Ubuntu/etc' menu, it stalls after that.

> **zia.newversion said:**
> Also, what exactly do you mean by no-luck? Does it freeze exactly like that? Please enlighten us about the situation with the flash drive. If we can make booting with flash-drive work, perhaps a solution can be found. Aha, I *knew* I would leave out some important detail somewhere!  
Booting from USB: Made it to start screen, 5 white dots are flicking white...orange...white... 3 went orange, then it froze and wouldn't do anything.
Installing from USB: A similar thing happened... no opportunity for install or any options for anything, just loading screen that hangs.

> **zia.newversion said:**
> You must have done a lot of effort writing all that without the Copy-Paste option. Kudos that. Yeah, I don't know anything except that the devil is in the details.  I know the fastest way to troubleshoot microsoft is to google the jargon (Error 0X800CCC0E... ).  I had no idea what in there might help, so I just included everything!

We can get to a command prompt when it is asking which version we want to open up.  We don't run in to any trouble using that.

Thank you kindly for your help.

---

### Post by zia.newversion on 2011-05-20
HUMBLE OPINION
--------------
Well... I am once again asserting that I am not an expert. However, I think the USB from which you are installing is the root of the problem. Are you using the same USB Installation Disk that you used for the installation which later faulted? If yes, then maybe you need to re-write the USB drive with Ubuntu Natty image... And if you have already done that and it still doesn't work, maybe there is some problem in the hardware USB drive... You might wanna look into that as well.

I take it that you have access to another computer (from which you are writing on this thread). You'll need that other computer to perform a full diagnostic and repair.

Then there is the possibility of the image you are using being corrupted for some reason. You may download the new image, do the checksum to verify it's OK and then try.

Or the software that you are using to write the USB might be causing problem. Download it again and then try. (I know, it's weird, looks like everything is broken. But only one of them actually is). Also, donn't forget to check the USB for errors and format it completely before proceeding.

Also, there are very slim chances of this happening, but I guess you should check your computer hardware for faults (maybe there is some problem with HDD, "Oh dear God...")... In any case, you can do that by trying to boot with the live disk of some other distro or maybe Windows... If that boots fine then "Oh thank God" there is no problem with your computer hardware. So one of the above steps should work. If they don't, you can't blame me... Coz hey, I already said, I am not an expert. :p JK, they should definitely work.


FRIENDLY ADVICE
---------------
Also, might I suggest that you create a swap partition if you succeed installing Ubuntu. I have looked into it a bit and I think the computer hung because of memory running out and no swap. And then when you cold-booted the system, some integral component or service of kernel got lost with it (black magic :p)... So if you didn't create a swap last time, you might want to do it this time. (The option for creating a swap partition is given while installing. Swap can be created after installation, too, but that'd be a little difficult.)

---

### Post by feag on 2011-05-20
The advice around here is certainly very friendly!
I have formatted my USB drive and I am looking back into how to install from a USB.  
Partitioning is something I have often had trouble finding useful information about.  I'm currently eyeballing this thread : [http://ubuntuforums.org/showthread.php?t=439236](http://ubuntuforums.org/showthread.php?t=439236) 
> You'll need two partitions (root, swap) for the basic set up. Root should be formatted as ext3 and swap is not formatted.Is that right?  Last time I installed I looked at the partitions because I wanted to do a dual-boot.  There wasn't an option for it, so I skipped it and did a full Ubuntu install with whatever default partition arrangement goes with it (I assumed it would just over-write everything however it wanted).

Thank you for your help.

---

### Post by zia.newversion on 2011-05-20
Partitioning is something most of the people who start using Linux/Ubuntu get stuck on. It is very easy once you know the concepts behind it.

If you want to "dual boot", chances are, you don't have extra space on your hard drive for swap drive. Well, you're in luck, because you don't necessarily need a partition for swap, you can just use a file for swap. I assume you have a little knowledge of computer basics, so you'd know what virtual memory or paging file in Windows is.

In Linux, it is preferred to have a separate partition for swap (against using a file in the root drive, like in Windows: pagefile.sys = Virtual Memory -> Location = C:\)... In Linux, you have a root partition (represented by /) and a swap partition for the most basic setup.

However, if you want to stick to that Windows analogy of Virtual Memory, or don't want to have to allocate separate partition for swap, you can declare a file as a swap-space. It is a bit tricky, but not that much.

You just install Ubuntu on your system allocating only one partition for root (/). (The installation process will warn about no swap space but ignore it. Once your Ubuntu system is up and running, you visit **_[COLOR="DarkRed"][this Wiki here]("https://help.ubuntu.com/community/SwapFaq")[/COLOR]_** and follow the steps listed... They are very easy and explanation is provided before every direction. It's worth a visit.

---

### Post by zia.newversion on 2011-05-20
And by the way, go for Ext4 instead of Ext3... It's newer, hence it is might be more robust and suitable for Natty.

---

### Post by feag on 2011-05-20
Okay sooooo....

1) Ran all the compaq memory tests, no problems.

2) Formatted USB drive, downloaded natty again (ran it through the checksum),  ran fresh Universal USB installer, tried installing.
Boot from usb flash drive, no problem.  Selected 'Install Ubuntu on a Hard Disk'.  Loading casper... lots of text scrolling over screen... get to ubuntu loading page, orange and white lights flash over eachother, eventually it just stops.

Time to try a different distro, I guess.

---

### Post by NormanFLinux on 2011-05-20
It could be your USB stick went bad. Buy a new one, install Natty on that and see if it will run the installer program. That happened to me after Ubiquity hanged on the first install screen on my old USB stick.

I discovered that can make a real difference and I now I am running Natty on both my netbook and my laptop with no problems.

---

### Post by linuxinstalledfromhdd on 2011-05-20
USB sticks can go bad very quickly. Try using a installation disc.

---

### Post by zia.newversion on 2011-05-21
> **NormanFLinux said:**
> It could be your USB stick went bad. Buy a new one, install Natty on that and see if it will run the installer program. That happened to me after Ubiquity hanged on the first install screen on my old USB stick.

I discovered that can make a real difference and I now I am running Natty on both my netbook and my laptop with no problems.

> **linuxinstalledfromhdd said:**
> USB sticks can go bad very quickly. Try using a installation disc.

+1: Did I mention that in my post? But there might be a problem with the USB drive... Look into that as well...
Back in Jaunty days, there was this UNetBootin (still is)... I tried installing with half a dozen USB drives by writing with UNetBootin but no luck... Either the USB didn't boot or it did boot but some error came up during installation. I dropped installation from USB and went back to CD installation. However, I later discovered that some of those drives didn't support BIOS booting and others were not compatible with something or other either... So, installation from USB may be faster and more convenient, but definitely not easiest.

---

