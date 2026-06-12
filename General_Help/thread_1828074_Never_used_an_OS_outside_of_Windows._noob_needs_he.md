---
title: "Never used an OS outside of Windows. noob needs help"
date: 2011-08-18
forum: General Help
---

### Post by HipsterZach on 2011-08-18
Hello everyone, I hope my questions are accepted with open arms and can be answered well. 

I have never messed around with OS installs apart from re installing Win XP one time. Quite frankly, I detest Windows, and need a change. I want to know a few things:


[LIST=1]
[*]If I can install Ubuntu without loosing any data in Windows 7
[*]If at any point I am not satisfied with Ubuntu, I can re install Win 7 and remove Ubuntu.
[/LIST]
I am also not to familiar with "dual booting". Would both OS's be installed at once? I would imagine that would cause problems, but I am not expert. 

Thanks for your help in advance!

---

### Post by Ms_Angel_D on 2011-08-18
Hello and welcome.

First off you might want to look into checking ubuntu out in a virtual install this way you haven't changed anything on your computer.

[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

if that's not really an option there is always a Wubi install

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

either way should allow you to take Ubuntu for a spin without worrying about messing up your current windows install.

also there is a dualboot which is a little more tricky and requires partition editing: [http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

a few more thoughts; you might also want to have a look at the ubuntu pocket guide. It's a free downloadable PDF book geared at introducing people to Ubuntu.

[http://www.ubuntupocketguide.com](http://www.ubuntupocketguide.com)

another good read is 

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

and finally
The Perfect Desktop - Ubuntu 11.04: [http://www.howtoforge.com/the-perfect-desktop-ubuntu-11.04-natty-narwhal-with-ubuntu-classic](http://www.howtoforge.com/the-perfect-desktop-ubuntu-11.04-natty-narwhal-with-ubuntu-classic)

---

### Post by dave01945 on 2011-08-18
if you install it as a dual boot then both os will be accessible from an initial startup menu

if you need to make a new partition using your windows 7 hard drive it's always recommended to backup any data first it is possible to create a new partition with empty space on a drive but always best to take precautions.

if you are unhappy with ubuntu it can always be removed but if you dual boot it you will have access to both

---

### Post by Basher101 on 2011-08-18
Hello,
Ofcourse dualboot works! all you need is just a ***_seperate_*** partition where your other OS can live. You are using Windows 7 right? you can easily free Hard disk space to install ubuntu on a new partition. Another method would be to install it on a USB stick (though this requires some expirience in partitioning)

---

### Post by sanderd17 on 2011-08-18
1. There are two methods of installing Ubuntu next to Windows.

The first method is called a "Wubi installation". That way you install Ubuntu as a program inside windows. When Windows boot, you can choose to go to Ubuntu.

This method is very suited for testing periods from 1 month to 6 months. If you use it longer, it will become unstable due to problems between the Windows filesystem and Ubuntu.

The second method is called a dual boot. You burn Ubuntu to a disk, you boot from that disk and in the installer you choose to "install Ubuntu next to Windows". This will be more stable, but it's more difficult to remove Ubuntu afterwards.

Dual booting gives absolutely no problems (I'm tripple booting right now).

2. You will normally not remove win7. But reinstalling is always possible.

Some tips:
[LIST]
[*]Always backup your important data
[*]try the live CD before you install (that's right, you can try ubuntu without installing, but it's a lot slower, just see if most things work)
[*]defragment windows before you install a dual boot or change partitions
[/LIST]

---

### Post by Basher101 on 2011-08-18
@sanderd17 the ubuntu installer wont give the "install next to windows" option if you dont free up enough space. I had to manually set things to install it on a 20GB partition. I once wanted to know how much % of the hard drive must be free (or is it a certain GB mark?) to give "install next to windows" option, but i had not the time to partition my hdd over and over to find out.

---

### Post by HipsterZach on 2011-08-18
So no one here recommends uninstalling Windows 7?

---

### Post by sanderd17 on 2011-08-18
> **HipsterZach said:**
> So no one here recommends uninstalling Windows 7?

Off coarse not, getting rid of windows asks some time. You need to find alternatives for all your apps (easy for most apps, hard for some). So until you're perfectly comfortable with Ubuntu, you should still have Windows around.

---

### Post by Ms_Angel_D on 2011-08-18
> **HipsterZach said:**
> So no one here recommends uninstalling Windows 7?

What we do recommend is using what feels comfortable to you, and how can you know if Ubuntu is right for you if you have never tried it?

Ubuntu is about choice and it's your choice as to how you wish to experience it. There have been some people who jumped straight in and just wiped windows from day one and were glad they did, others however have not been so happy with their choice.

either way I recommend checking it out first just to get an idea of whether it's for you or not.

---

### Post by HipsterZach on 2011-08-18
Of course I would never uninstall Windows 7 without trying Ubuntu first! haha. 

Thank you all for this information. I will be sure to give it a shot once I go down to the store for some blank CD's. :D

---

### Post by Elfy on 2011-08-18
> **HipsterZach said:**
> So no one here recommends uninstalling Windows 7?

I'd not do that - or rather I'd not do that straight away, took about 2 versions of ubuntu before I could be bothered to go and retrieve the unused windows space.

I'd wait until I was sure. 

Not read all the posts in detail here - but I would not recommend wubi but a real dual boot. 

Also - use the windows disk management thing to free up some space if you do go the real dualboot road. 

Good luck :)

---

### Post by Topsiho on 2011-08-18
I agree with posters before me: dual boot next to Windows, and keep Windows, for two reasons: a) get comfortable with Ubuntu (or any other Linux) first, and b) sometimes you still need it, for 1) if you use a Windows program that doesn't run well in Ubuntu (sometimes you can use wine to try and do that), and 2) most or all electronic devices are sold with auxiliary programs fit for Windows only (such as my TomTom, for updating satellite positions, otherwise the DomDom (DumbDumb) will not find a position).

What I really want to say here, and is not mentioned yet, (sorry, it is :0) is that if you want to install Ubuntu next to Windows, you should create space for Ubuntu ***using Windows itself***. If not, you risk that Windows will not boot after installing Ubuntu, as it finds a situation that it doesn't know. If you are lucky it boots, but it takes hours to do so first time, as the disk is checked. Before shrinking a disk in Windows, be sure to defagment it first a number of times, so that you are sure that all data in it is only in the first part of it.

As for space you need: if your disk is large enough I would say that 10GB is plenty for / (root partition), twice your RAM for the swap partition, and any amount of space for your /home partiton, which will hold your personal data and settings (configurations).

ALLWAYS BACK UP YOUR PRECIOUS DATA FIRST any time you do an install. One never knows.

Topsiho

---

### Post by oldfred on 2011-08-18
Another alternative is just to do a full install to a flash drive. It will not be quite as fast both as USB ports are slower than SATA ports and flash is not as fast as a hard drive.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I stopped using CDs for installs and now only use USB flash drives. Smaller ones for installing and large one's ( 8GB or more) for full installs. 

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Have a way to repair every system you install with a repair CD, liveCD or other Linux repair tools.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by Basher101 on 2011-08-18
i think the previous posters have mentioned the most important things. i really should bookmark links to guides tomorrow to avoid explainig basics as dualboot installations over and over...ill take a look on those guides and bookmark them and/or just copy&paste the important stuff to new folks.

---

### Post by HipsterZach on 2011-08-18
> **oldfred said:**
> Another alternative is just to do a full install to a flash drive. It will not be quite as fast both as USB ports are slower than SATA ports and flash is not as fast as a hard drive.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

I stopped using CDs for installs and now only use USB flash drives. Smaller ones for installing and large one's ( 8GB or more) for full installs. 

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

Have a way to repair every system you install with a repair CD, liveCD or other Linux repair tools.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)


Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

O.O Is all that necessary?

---

### Post by oldfred on 2011-08-18
No, my Boss always complained I gave him too much information also.

But some want more info and others just want a quick fix without really understanding why. Some want alternatives, others are happy with just do it this way and you will be ok.

You can pick and choose what you want to do or how you do it. But if you do not have backups and a way to repair your system, you do not have any valuable information on your computer.

---

### Post by 3rdalbum on 2011-08-19
You can remove Windows when you feel like you can do without it.

Note that it's not a case of "Uninstalling" Windows, i.e. there's no specific "uninstall" procedure. Merely erasing the Windows partition will get rid of Windows from your system. It only takes a couple of seconds, but of course it also erases the data on that partition; backing up this data that you want to keep is what is time-consuming about it all :-)

---

### Post by mastablasta on 2011-08-19
> **HipsterZach said:**
>  
Thank you all for this information. I will be sure to give it a shot once I go down to the store for some blank CD's. :D
 
if your computer has an option to boot form USB then it's much safer and faster to create a liveUSB instead of liveCD. 1GB USB key will do. to make this process easy there are at least 2 very simple and good programmes:
[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
 
 
what you do is basically select the image you downloaded, then if you want to set some permanent file (to keep some settings even after reboot - as normal live boot moves everything to RAM and then erases everything on reboot), click next and all is done for you. then you just boot from USB and you have a system. ok it works in RAM, but with persistence file you get to keep some settings you made. very good for testing the OS.

---

### Post by CrusaderAD on 2011-08-19
+1 for dual booting. Wubi works too, but I've encounters issues with that before. Dual booting is a little more work, but worth it.

---

### Post by HipsterZach on 2011-08-19
Thank you all so much :D This will be my next weekend project.

---

### Post by flipper T on 2011-08-19
if it takes you more than 20 minutes, you are doing it wrong.

:)

---

### Post by paxxus on 2011-08-19
I tried wibi but I didn't think I was the right choice. I'd recommend a real dual boot setup. It can take longer than 20 minutes though, especially if you need to shrink your Windows 7 partition, which you most likely will have to. I think the ubuntu installer can do that but I didn't dare it, so it did it from Windows 7. Here are my notes (remember to backup your important data first!):

### Shrink Windows Partition ###

Print out these links:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
[https://help.ubuntu.com/community/RecoveringWindows](https://help.ubuntu.com/community/RecoveringWindows)

From Windows:
* Disable the page file:
    Go into Control Panel and in 'System', 'System
    Properties', and then 'Advanced' tab, look for the 'Performance Settings'
    button. In the Advanced tab look for 'virtual memory' and be sure to take
    note of your settings on paper before making any changes. Then click the
    button for 'no paging file' and click 'Apply'.
* Disable System Protection
    Control Panel -> System and Security -> System -> System Protection
    Make sure to delete any saved recovery files.
* Reboot.
* Check disk (you'll have to reboot in order to perform the scheduler check).
* Defragment drive C.
* Shrink drive C to make room for Ubuntu.
    Settings -> Control Panel -> Administrative Tools -> Computer Management ->
    Storage -> Disk Management -> Shrink Volume
    You'll need at least 20GB for ubuntu but more is better. I freed up about
    80GB for ubuntu leaving about 60GB for Windows (it currently uses 38GB).
    If you cannot shrink the drive enough even though you have plenty of
    free space, then you might try the trial version of PerfectDisk which
    you can download from the web (use the "Prep for Shrink" command).
* Reboot. Very important! This lets the Windows boot manager see and adapt
  to the resized partition. See that all is good then reboot again just to
  make sure.
* Enable System Protection
* Enable the page file (choose 10%).
* Done.


Note: In case you are wondering, the (temporary) disabling of the page file and recovery file (plus deletion of saved recovery files) was needed because these files are unmovable by the defragmentation tool. I had a big fat recovery file almost at the end of my Windows 7 partition preventing me from shrinking more than a few GB.

---

### Post by sanderd17 on 2011-08-19
if you want to set up everything properly, it can take long, especially until you understand what other people mean :D.

---

