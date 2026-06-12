---
title: "dual booting win 7 and ubuntu 11.10"
date: 2012-03-11
forum: General Help
---

### Post by gamboa123 on 2012-03-11
evening all, i'm new to this forum and new to ubuntu So a Big HELLO to you all 
 
I attempted my first dual boot today on the girlfriends pc, i'm a complete newbie with this so bare with me please i'll try to explain the problem :(

Have a PC with 2 h/d's, its got 2gb ram

 1st 120gb 2nd 160 gb, installed win 7 pro on the first with no worries.

on 2nd drive I used ubuntu 11.10 to partition as follows - 1st partition = primary 6gb using / 
2nd partition = logical 2gb swap area
3rd partition = remaining free space set up as (primary i think) /home 

boot loader for ubuntu was saved on 2nd drive with ubuntu, then i used **easy bcd** to add ubuntu to the win 7 boot loader and make it the default o/s on boot up.

Ok so windows loads up fine, but when i boot into ubuntu i just get a (only way i can describe it is) grub command prompt screen??  looks something like      grub:- 

In all honestly i don't know anything about ubuntu have never used it at all, and have only been following a tutorial online on how to do the dual boot, so if any one knows where i have gone wrong any advice would be great.  

Possibally its the partitioning but I don't really understand what i'm doing so only guessing

thanks for the help guys and girls

---

### Post by lrgmmc on 2012-03-11
can you select the 160 Gb drive as the one to boot from when you turn on your pc. I mean from the bios.

---

### Post by gamboa123 on 2012-03-12
i'm not sure, when i go into the bios, only 1 drive shows up as the primary ide master, theres no primary ide salve which i guess should be the 2nd drive? I think the 2nd drive shows up in the bios boot sequence page but when i select it as first in the list it won't boot from it? surely if the 2nd drive isn't showing as a slave i shouldn't be able to access, partition and install on it?  

its got a asus A7V880 board with AMI bios if that makes any difference?

thanks

---

### Post by Mark Phelps on 2012-03-12
Since you have two IDE drives, the solution I would recommend is the following:
1) Open the case to see the drives
2) One drive will be jumpered Master, the other Slave
3) Switch the jumpers on the drives
4) Also switch the cable connections
5) Close the case and reboot
6) You should be booting into the Ubuntu drive now

If this works, then once in Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB config file and when you then reboot, you should be presented with a GRUB menu.

---

### Post by gamboa123 on 2012-03-12
i've opened it up and had a look, it appears the drives have completley different connections for both power and ide?   not sure where to go from here.

---

### Post by dave2001 on 2012-03-12
Hi Gamboa, 
Welcome to Ubuntu and the forums! Ubuntu can be great fun, and very useful, but it can also have a steep learning curve in the beginning! Your process for installation of a dual-boot system sounds very similar to what I did on one of my machines. So your definitely headed in the right direction.

I have a few questions to help clarify the situation.

1. After downloading an Ubuntu install CD iso, did you verify it with an md5sum? Did the CD you burned from the iso get verified afterwards? Even small corruptions in the file during download or burning can create a non-functional installation.

2. Have you tried running the LiveCD of Ubuntu 11.10 on this computer? If so, how did it run? Were there any issues or non-working hardware?

3. Was this computer set up differently previous to this, or did you just recently build/buy it? If it was set up differently before, how so?

---

### Post by gamboa123 on 2012-03-12
hi dave

Hello Dave I'll try to clarify best i can.

1. No i didn't verify the ubuntu iso where do i get md5sum from? any links?

2. it did already have ubuntu installed on one of the hard drives and seemed to work ok,  but i'm not sure which drive it was on becuase i didn't do the install of it.

3. i beleive it was an off the shelve pc just with an extra h/d added, the 160gb drive, which was added by my girlfriends dad.   

I'm thinking the problem is that 2nd drive isn't showing up as the slave drive in the bios, but then how i am able to access it when i install ubuntu on it????


thankyou

---

### Post by dave2001 on 2012-03-12
Here's a link for the Oneiric release page, which has all the different versions: [http://releases.ubuntu.com/11.10/](http://releases.ubuntu.com/11.10/)

On each release page you'll find an md5sum file near the bottom, but here's a direct link to make it easier:
[http://releases.ubuntu.com/11.10/MD5SUMS](http://releases.ubuntu.com/11.10/MD5SUMS)

If you've never done an md5sum check before, there's a simple (and free) windows utility you can use, since you have a working windows install already: [http://download.cnet.com/HashCalc/3000-2250_4-10130770.html](http://download.cnet.com/HashCalc/3000-2250_4-10130770.html)

Also, if both your drives have separate connections to the mobo, you may not have a master and slave drive. The master/slave combo is only needed when two ide drives have to share a connection or channel.

To reduce possible errors and complications, I would physically remove the first drive (with windows successfully installed on it). Then, try re-installing ubuntu on the remaining drive. Boot the computer and make sure ubuntu works properly. Then add back in your first drive, boot to windows and rerun easyBCD.

---

### Post by oldfred on 2012-03-12
If you do reinstall make / (root) a bit bigger. Only if you do not have room should it be as small as you made it. I normally suggest 10 to 25GB for / depending on your hard drive space that you have for Ubuntu.

Does BIOS show that you can boot from either drive? Some newer IDE systems let you choose. All SATA systems have to let you choose as there are no settings on drive.

If you want to know which type of drive you have:
with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

To see where everything is installed, post link to boot info script from Boot-Repair:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by gamboa123 on 2012-03-12
Dave
 i've downloaded another ubuntu iso from your link and checked it with the hash check program everything fine with that.  

yes the hard drives are connected to the mother board seperatly i think, one has a very wide connection and the other 160gb drive has a differenet style much smaller connection which links to the mobo in a different place.

i will try unplugging the windows drive and re-installing ubuntu and see what happens


cheers

---

### Post by gamboa123 on 2012-03-12
Hello oldfred thanks for trying to help


I will do as you say on the re-install and make the / a bit bigger

Yes i believe the bios shows i can boot from both drives, they both show up in the boot seqeunce option in bios anyway?

looks like i have 1 parallel hd (one with win 7 on)
and the drive with ubuntu is a seriel drive

I think the dvd drive is plugged into the other parallel port

I was trying to do a boot info script yesterday but got a bit lost with if i'm honest.

i'll take another look at it tonight.


thanks for the help

---

### Post by oldfred on 2012-03-12
With mixed PATA/SATA systems drive order can get mixed up. Often BIOS will promote PATA drive to sda. If your sda is PATA/Windows and you keep it as sda then you should not have any issue. 

Ubuntu can install to a stand alone drive and then when you plug in Windows it will not get confused as it uses UUIDs not devices like /dev/sda.

But you will have to run this in Ubuntu to find Windows after plugging the Windows drive back in. And in BIOS choose to boot the Ubuntu drive.

```
sudo update-grub
```

---

### Post by gamboa123 on 2012-03-12
ok I disconnected the hard drive with windows on it reinstalled ubuntu on the other drive, ubuntu works fine, when i try to boot up windows i just get a blank black screen with a - sign that keeps blinking?

i'm just gonna try the boot repair thing 

wish me luck!

---

### Post by gamboa123 on 2012-03-12
ok got the boot report thingy if someone can take a look at it and firgure it out, all looks greek to me :sad:

[://paste.ubuntu.com/880810/]("http://ubuntuforums.org/://paste.ubuntu.com/880810/")


thanks

---

### Post by oldfred on 2012-03-12
Link is not correct. extra // ?

is this yours:
[http://paste.ubuntu.com/880810/](http://paste.ubuntu.com/880810/)

How are you booting Windows? 

You must have had the sdb or 122GB drive as sdb when you installed Windows and sda as the boot drive. Windows 7 installed its hidden 100MB boot/repair partition in sda1, but your main install is in sdb1.

Windows does not have to have the separate boot partition and with a Windows repairCd or USB you can repair your install in sdb. Some have copied the boot files bootmgr & /boot/BCD to the main install and run repairs to fix it also.

---

### Post by gamboa123 on 2012-03-12
yes thats the one,  windows doesn't boot now.

Any links for windows repair cd?  i'm trying to use the windows dvd but it doesn't seem to repair anything?

---

### Post by oldfred on 2012-03-12
If we get a chance we suggest you make your Windows repairCD right away when Windows still works. But you may be able to install a Windows work alike boot loader and boot Windows. You will have to reinstall grub2's boot loader to the MBR of sda later. And you will need the Ubuntu liveCD to reinstall grub2's boot loader.

New versions of Ubuntu may not have synaptic.

sudo apt-get install synaptic

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.
You should also install to sdb
sudo lilo -M /dev/sdb mbr

We used to recommend this site for a Windows repairCD, but now they charge $10.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links (Now $10.00):
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

If you get Windows booting make your repairCD or if you know someone booting 32bit or 64bit whichevey you have:

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

