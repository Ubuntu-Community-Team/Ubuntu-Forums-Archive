---
title: "Ubuntu 10.10 won't boot"
date: 2011-04-09
forum: General Help
---

### Post by searchfgold6789 on 2011-04-09
Hi,
I'm hoping you can help me with this situation. Thanks for your time in reading this post.
I just got a new PC - an eMachines. It's got a celeron D 2.66 Ghz, 1.5 GB of RAM, and a PCI graphics card I added later because the onboard graphics weren't working. I also hooked up a PCI to IDE adapter - the BIOS does not formally recognize any of the devices hooked up to that, but the Kubuntu Live CD recognizes all of them just fine; I don't plan on booting anything from there.
My problem is, once I have installed Kubuntu and reboot, I select Ubuntu and it tries to boot but nothing appears except for a blinking cursor. When I type anything it doesn't appear; I have no chioce but to do a hard reboot.
Recovery Mode does basically the same thing. Windows XP boots fine.
I'm stumped! But I knew this would be just the place to find the best advice as to what I should do next.
The results from the Boot Info Script are attached. Oddly, lshw gives an "Input/Output Error" ... Wonder what that could be...

---

### Post by SeijiSensei on 2011-04-09
It appears you have two hard drives and have installed (different versions of) grub on them both.  Only one drive will be booted, and it's usually the one called /dev/sda.  I suspect you told the installer to install grub on the master boot record of the second drive, /dev/sdb.  Even if Kubuntu is installed on /dev/sdb you need to have the installer put grub on the MBR on /dev/sda to handle booting for both disks.

---

### Post by searchfgold6789 on 2011-04-09
> **SeijiSensei said:**
> It appears you have two hard drives and have installed (different versions of) grub on them both.  Only one drive will be booted, and it's usually the one called /dev/sda.  I suspect you told the installer to install grub on the master boot record of the second drive, /dev/sdb.  Even if Kubuntu is installed on /dev/sdb you need to have the installer put grub on the MBR on /dev/sda to handle booting for both disks.

Thanks! Does this mean I should proceed to install grub on /dev/sdb and /dev/sda? I believe I actually intended for the installer to only put grub on /dev/sda, but heck computers do what you tell them to do, not what you want them to.

I guess what I'm saying is, what should I do now?
 - search

---

### Post by SeijiSensei on 2011-04-09
> **searchfgold6789 said:**
> I guess what I'm saying is, what should I do now?

I guess we need to know what you're trying to do.  It looked from that text file that you have two different Ubuntus and an Windows partition?  Is that what you want, or do you just want XP and Kubuntu?  If the latter, just install Kubuntu again and make sure to specify /dev/sda as the location for the grub installation.  It's certainly possible to have grub on /dev/sda and still use /dev/sdb1 as the root filesystem for Linux.

Have you booted from the installation CD in its "Live" mode to make sure all the hardware on this machine is supported?  That's an important first step for troubleshooting since we can then rule out hardware issues.

---

### Post by searchfgold6789 on 2011-04-10
I am currently posting from a Live CD. All of my hardware is detected; I can read and write to each of my hard disks, mount them, and partition them.
[LIST]
[*]The disk with two ext4 partitions on it contains data I want to retain in the future but I don't need to boot from this disk.
[*]The hard disk with the solo NTFS Partition is Windows.
[*]The one with the extended partition and the extra ext4 partition is for Kubuntu which is in the extended one and all of the data from my home folder from my other computer that I'm migrating from in the extra one.
[/LIST]
I'm going to install Kubuntu again now :)
Thanks again,
 - search

---

### Post by searchfgold6789 on 2011-04-13
I reinstalled Kubuntu and everything went fine and dandy - Kubuntu booted without me having to configure anything.
Then, there was a partition on the same hard disk as my / which I wanted to get rid of; I didn't need it anymore because I had copied the contents to a USB stick. I removed the partition and then made my / partition fill the hard disk and am now back at square one :(. I tried reinstalling Kubuntu five times, all with the same results - Grub appears to be fine (no countdown which is weird); when I try to boot Kubuntu all that appears is a blinking underscore; when I try recovery mode all that appears is lines of code for about 30 seconds and then white vertical lines appear on the screen. The Kubuntu live CD boots and detects all of my hardware, but oddly enough the Xubuntu live CD cannot boot: I tried booting it three times, once it ran for a while and then displayed half of the desktop background for the Kubuntu live cd, the second time it booted and displayed the correct desktop background except with an X for a mouse cursor and nothing else, the third time there was only a black screen.
Attached is a fresh boot info script results file (/dev/sdh is a thumb drive).
Here is my hardware:
2.66 Ghz Celeron D
1.5 GB DDR SDRAM memory
Wireless, ethernet, PCI graphics card (added because the onboard one was failing)
500 watt power supply
CD reader, dvd reader, and dvd writer drives
I appreciate the help with this confusing problem!

---

### Post by searchfgold6789 on 2011-04-13
Does the power supply have something to do with it?

---

### Post by Dutch70 on 2011-04-13
I doubt the power supply would have anything to do with it, but what makes you ask?

It sounds more like your graphics card which you never did say which one you have, just that it's PCI.

You may want to try nomodeset or other boot options.
[[COLOR="RoyalBlue"]How to set NOMODESET[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="RoyalBlue"]LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")

Are you using 10.04 or 10.10?

.

---

### Post by searchfgold6789 on 2011-04-13
[QUOTE=Dutch70]I doubt the power supply would have anything to do with it, but what makes you ask?[/quote]Oh - I just heard somewhere that there is such thing as Too Much Wattage For A PC. Also, sometimes Linux gets Decompression errors when using a power supply that has residual power problems. I guess I misheard :)
[QUOTE=Dutch70]
It sounds more like your graphics card which you never did say which one you have, just that it's PCI.
[/quote]The hardware lister says that it's a ATI Radeon RV100 QY [Radeon 700/VE][quote=Dutch70]
You may want to try nomodeset or other boot options.
[[COLOR=RoyalBlue]How to set NOMODESET[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR=RoyalBlue]LiveCDBootOptions[/COLOR]]("https://help.ubuntu.com/community/LiveCDBootOptions")
[/quote]Thanks, I'll try that now![quote=Dutch70]
Are you using 10.04 or 10.10?

.[/QUOTE]
Kubuntu 10.10; thanks for the suggestion and the links - I'll get back with the results!

---

### Post by searchfgold6789 on 2011-04-13
[SIZE=4]You Rock, nomodeset worked![/SIZE]
Thank you SO MUCH for the handy suggestion! Probably saved me hours of headache. :P

---

### Post by Dutch70 on 2011-04-14
Great! Glad to hear you've got it all worked out. :)
and you're quite welcome.

See ya around the boards
Dutch

---

