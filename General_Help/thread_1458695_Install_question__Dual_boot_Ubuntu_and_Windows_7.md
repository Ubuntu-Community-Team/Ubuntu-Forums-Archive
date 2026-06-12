---
title: "Install question | Dual boot Ubuntu and Windows 7"
date: 2010-04-20
forum: General Help
---

### Post by specialalaa on 2010-04-20
Hi. I'm new to Ubuntu. I'm on Windows 7 64-bit, and I want to install and dual boot ubuntu 9.10 with Windows 7...
A quote from ubuntuguide.org:
> Warning: Ubuntu Desktop edition installer no longer allows a custom installation of GRUB, and it now uses GRUB2 (which allows very little customization). DO NOT USE the Karmic Koala Desktop edition if you use a boot partition, use multiple OS (more than 2), or chainload bootloaders. The Ubuntu installer will overwrite your Master Boot Record and you will later be forced to recreate it. This is a serious flaw in Karmic Koala. Use the Ubuntu Server edition instead (and then later add the ubuntu-desktop).

These instructions **[listed in the site]** are for installing more than two operating systems on your hard drive. If you only need two operating systems (such as a Windows installation and a (K)ubuntu Linux installation), it is easiest to just use the (K)ubuntu installer to do it for you (as detailed on the main page).
I know that: (K)ubuntu installer to do it for you == select "install to the **largest available free space**" in the install through LiveCD, of course after creating unpartitioned space in my hard disk (preferably 20GB+).. 

My question is: given the warning mentioned in the quote above, do I still need to use Ubuntu Server edition even if I'm going for the aforementioned easy way? Or can I just go with the Desktop edition and it'll install fine, without messing up the MBR...

---

### Post by Mark Phelps on 2010-04-20
From what I recall, the Alternate CD provided the option of specifying where to install the GRUB loader files -- at least, it did in older versions.  I don't believe the Desktop CD provides that option.

---

### Post by oldfred on 2010-04-20
I have done just about everything they give a warning about. If anything grub2 is more customizable, but it was new with Karmic and we are learning about it, where grub legacy had not been maintained for years and could not support many new system features. I had no trouble installing with the standard desktop to both my desktop and to my laptop.

All new system installs overwrite the MBR since they assume you want to boot the new system. Windows does it without telling you. Grub does give you a choice but you have to know to use the advanced button on the last partitioning screen before clicking the install button. It is not difficult to reinstall boot loaders as long as you have a liveCD or bootable USB with the installer.

IF you ever want to recover a MBR these are the instructions. I like to have several ways to boot computer when every I modify it, so I have several liveCDs and now a USB key with several more ISO system that I can boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If using win7 it is better to use the windows tools to shrink the windows partition and reboot windows several times so it can run chkdsk and recognize the new size. Leave at least 20-30% free space in windows or it will slow down or stop working.

Only if you have more than one drive would you want to select anything other than the MBR of the current drive. Do not install to the partitions unless you are really advanced and have multiple boot loaders that allow chainbooting.

---

### Post by specialalaa on 2010-05-10
> **oldfred said:**
> I have done just about everything they give a warning about. If anything grub2 is more customizable, but it was new with Karmic and we are learning about it, where grub legacy had not been maintained for years and could not support many new system features. I had no trouble installing with the standard desktop to both my desktop and to my laptop.

All new system installs overwrite the MBR since they assume you want to boot the new system. Windows does it without telling you. Grub does give you a choice but you have to know to use the advanced button on the last partitioning screen before clicking the install button. It is not difficult to reinstall boot loaders as long as you have a liveCD or bootable USB with the installer.

IF you ever want to recover a MBR these are the instructions. I like to have several ways to boot computer when every I modify it, so I have several liveCDs and now a USB key with several more ISO system that I can boot.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If using win7 it is better to use the windows tools to shrink the windows partition and reboot windows several times so it can run chkdsk and recognize the new size. Leave at least 20-30% free space in windows or it will slow down or stop working.

Only if you have more than one drive would you want to select anything other than the MBR of the current drive. Do not install to the partitions unless you are really advanced and have multiple boot loaders that allow chainbooting.
The "Advanced" button isn't really that advanced =/, it just asks you where do you want to install GRUB2...

But I still did not get an honest answer to my original question... I'm planning to do the following, so I want to know if this will work or not:

*I'll download Ubuntu 10.04 LiveCD image and burn it.. On my Windows 7 64-bit, I will use a program to partition the hard disk to have a 20GB "unpartitioned space" (i.e. not partitioned to FAT or NTFS) at the end of the hard disk, call it sda7.. I will run chkdsk (I don't know why this step is important, but people say it is =D).. I will insert the LiveCD, and will choose "**Install Ubuntu to the largest free space available**" (or something of that sort).. At the last screen I will hit the "Advanced" button, and will choose to install GRUB2 on the Ubuntu partition (I am doing this because I do NOT want GRUB2 to be my main bootloader and overwrite the MBR), which will be sda7 (hd0,6 I think?? Or hd0,7? I only have one hard disk).. After installation, it will still boot into Windows because I have yet to add Ubuntu to the MBR; and this will be done through EasyBCD...*

Are these steps correct? Or am I missing something? 

Also, another question.. I have Windows 7 64-bit installed on the laptop which is running on 4GB of DDR3 RAM and 1GB ATi Radeon HD graphics card.. Can I use Ubuntu 10.04 32-bit and enable PAE? Or do I go for the 64-bit Ubuntu? I do NOT want to go through the hassle of trying to get things to work on 64-bit.. I will NOT be using Ubuntu for video editing and heavy stuff, I just want to get familiar with it because it looks cool =).. Having said all that, dual booting Windows 64-bit with Ubuntu 32-bit will not cause an issue right?

---

### Post by pcdave98 on 2010-05-10
I was also new to Ubuntu, a couple of months ago, and fancied giving it a try. I shrunk my Win 7 64 bit partition using the windows disk utility thingymebob - I left 100 gigs free as my hard disk is quite large. Then I made a bootable USB for 9.10 64 bit and installed it in the space I'd made.

An idiot could do it. In fact - I did.

:P

I've upgraded to 10.04 since then and both versions have been superb. I'd bin Windows completely but for my iPhone and TomTom.

---

### Post by specialalaa on 2010-05-10
> **pcdave98 said:**
> I was also new to Ubuntu, a couple of months ago, and fancied giving it a try. I shrunk my Win 7 64 bit partition using the windows disk utility thingymebob - I left 100 gigs free as my hard disk is quite large. Then I made a bootable USB for 9.10 64 bit and installed it in the space I'd made.

And idiot could do it. In fact - I did.

:P

I've upgraded to 10.04 since then and both versions have been superb. I'd bin Windows completely but for my iPhone and TomTom.
So shrinking the partition with any tool through Windows works, right? (I'm planning to use EASEUS Partition Manager).. You chose "Install to largest free space" when you were installing it?

Lol @ "I'd bin Windows".. iTunes doesn't work on Ubuntu? =(..

---

### Post by pcdave98 on 2010-05-10
> **specialalaa said:**
> So shrinking the partition with any tool through Windows works, right? (I'm planning to use EASEUS Partition Manager).. You chose "Install to largest free space" when you were installing it?

Lol @ "I'd bin Windows".. iTunes doesn't work on Ubuntu? =(..

Control Panel>System and Security>Administrative Tools>Create and Format Hard Disk Partitions

Yes - I installed into 'largest Free Space'. 

I've not really put any effort into trying to get iTunes and TomTom working in Ubuntu. I've no idea if it is even possible. It just means I have to boot into Windows, every couple of weeks, for 30 minutes to update my Sat Nav and back up my iPhone. I update Windows at the same time - then head straight back to Ubuntu.

:)

---

### Post by tsubaki on 2010-05-10
the same works for 10.04 and as for the iTunes check the following link:
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

works in9.04 will check in 10.04

---

### Post by pcdave98 on 2010-05-10
> **tsubaki said:**
> the same works for 10.04 and as for the iTunes check the following link:
[http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html](http://www.ehow.com/how_5197743_download-itunes-linux-ubuntu.html)

works in9.04 will check in 10.04


Thanks - I think I might just give that a try.

:)

---

