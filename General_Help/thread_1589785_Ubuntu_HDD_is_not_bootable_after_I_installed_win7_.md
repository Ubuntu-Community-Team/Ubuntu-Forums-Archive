---
title: "Ubuntu HDD is not bootable after I installed win7 &amp; split it up?"
date: 2010-10-06
forum: General Help
---

### Post by PsychedelicWonders on 2010-10-06
Ok here is the scenario

At first I was running an 80g HDD with 2 partitions, 50g for win7 & 20g for Ubuntu.

I ran out of space & upgraded HDD's.

So now I have win7 working successfully on a new 500g HDD

And I've left Ubuntu on the 80g HDD, but when I try to boot up from it, it says:

Reboot & select proper boot device or insert boot media in selected boot device and press a key...

So this obviously means its unbootable for some reason... the question is, how do I fix it?

---

### Post by andrewthomas on 2010-10-06
You probably need to reinstall grub2 to it. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just to be sure go here 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and post the results with your reply.

---

### Post by PsychedelicWonders on 2010-10-06
> **andrewthomas said:**
> You probably need to reinstall grub2 to it. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Just to be sure go here 

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

and post the results with your reply.

the guy who helped me fix win7 and transfer hard drives said grub messes & corrupts windows boot?

so is there a way to do it without grub?  Although I will say I like the menu that grub offers...

---

### Post by PsychedelicWonders on 2010-10-06
He just said this:

Well install it for Ubuntu only if you can.

No need to add Windows 7 since you can boot them separately via BIOS Boot Menu.

It does only install for Ubuntu correct?  I mean now it is on a completely separate HDD all for itself...

---

### Post by oldfred on 2010-10-07
The issue is if you have only one drive and some windows software uses the same space on the drive to hide serial numbers or special info that it does not want you to see. The space is normally used for boot info, so it is the windows software that is the problem. 

But as long as you have two drives and install grub to the Ubuntu drive and have the windows boot loader in the windows drive, you will have no issues.

---

### Post by PsychedelicWonders on 2010-10-07
> **oldfred said:**
> The issue is if you have only one drive and some windows software uses the same space on the drive to hide serial numbers or special info that it does not want you to see. The space is normally used for boot info, so it is the windows software that is the problem. 

But as long as you have two drives and install grub to the Ubuntu drive and have the windows boot loader in the windows drive, you will have no issues.

Ok I'm going to try to fix it now then.

Do I want to make the Ubuntu HDD 1st boot?

---

### Post by PsychedelicWonders on 2010-10-07
Its been so long since I've used ubuntu, where do I find the device name/partitions so I make sure I'm choosing the right one?

---

### Post by PsychedelicWonders on 2010-10-07
hmm. I have a 64 & 32 Live Ubuntu cd that I made a while ago when I first installed the program

I tried both, but for some reason my dvd isnt opening the cd?  And yes I do have 1st boot to dvd & I even tried to force it via F8 in bios to get to BBS and choose dvd & it still just boots up to windows & not the live cd?

Any ideas?

I've also got a 16g usb available to use as a way to open a LiveCd if that will work?

---

### Post by PsychedelicWonders on 2010-10-07
> **PsychedelicWonders said:**
> hmm. I have a 64 & 32 Live Ubuntu cd that I made a while ago when I first installed the program

I tried both, but for some reason my dvd isnt opening the cd?  And yes I do have 1st boot to dvd & I even tried to force it via F8 in bios to get to BBS and choose dvd & it still just boots up to windows & not the live cd?

Any ideas?

I've also got a 16g usb available to use as a way to open a LiveCd if that will work?

Still stuck on this... I dont know what it could be why its not booting from either Ubuntu disk I have?

---

### Post by PsychedelicWonders on 2010-10-07
Ok I see via this:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

you can use a USB stick

And I can see how you get it ON the stick, but it doesnt tell you how to get your computer to see it as 1st boot during reboot?

Any ideas?

---

### Post by Quackers on 2010-10-07
That would be a setting in your pc's bios. The same one that is set to boot from cd - although something isn't working right there, if you can't boot from the Ubuntu cd.

---

### Post by soldier1st on 2010-10-07
> **PsychedelicWonders said:**
> Ok I see via this:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

you can use a USB stick

And I can see how you get it ON the stick, but it doesnt tell you how to get your computer to see it as 1st boot during reboot?

Any ideas?
your pc's BIOS must support booting from USB, otherwise it will not boot it. new pcs support it but older ones like mine does not.also in your pc's bios you need to set your cd drive as the first device to boot then set your HDD as your second so Ubuntu/Windows can see it and for Ubuntu if you installed the 32bit version use the 32bit version to boot from.
this site should provide help [http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/](http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/)

---

### Post by PsychedelicWonders on 2010-10-07
> **soldier1st said:**
> your pc's BIOS must support booting from USB, otherwise it will not boot it. new pcs support it but older ones like mine does not.also in your pc's bios you need to set your cd drive as the first device to boot then set your HDD as your second so Ubuntu/Windows can see it and for Ubuntu if you installed the 32bit version use the 32bit version to boot from.
this site should provide help [http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/](http://blog.linuxtracker.org/2009/12/17/how-to-recover-grub2-linux/)

No I have a newer computer, 2 years old only.

I tried to force it via BBS and make it start with the USB, as it did come up in the list.  But when it tried to load off of the USB I received an error message saying:

BOOTMGR missing

What does that mean & how do I fix it?

I followed all of the directions on this page:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by PsychedelicWonders on 2010-10-07
I should say I did get this error when trying to make the USB:

Any ideas why its giving me that error message?

---

### Post by PsychedelicWonders on 2010-10-07
Does anything special have to be done to the USB drive?  It was just a normal, workable drive...

---

### Post by PsychedelicWonders on 2010-10-07
Tried it again with no success...

---

### Post by oldfred on 2010-10-07
[https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482)

There seem to be a few bugs.
One older one is for larger USB drives it does not set LBA, so you need to reformat with gparted and set LBA flag.
U3 has to be turned off, if your WSB has it.
I think there were some syslinux versions issues where you had to remove something in the file but cannot find that now.

I just use grub2 to loopmount the ISO and that works well for me. But you need linux to install grub2 to the flash drive.

---

### Post by PsychedelicWonders on 2010-10-07
> **oldfred said:**
> [https://bugs.launchpad.net/ubuntu/+source/usb-creator](https://bugs.launchpad.net/ubuntu/+source/usb-creator)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/458482)

There seem to be a few bugs.
One older one is for larger USB drives it does not set LBA, so you need to reformat with gparted and set LBA flag.
U3 has to be turned off, if your WSB has it.
I think there were some syslinux versions issues where you had to remove something in the file but cannot find that now.

I just use grub2 to loopmount the ISO and that works well for me. But you need linux to install grub2 to the flash drive.

Yeah I was getting some kind of syslinux error too...

So how do I fix this?

For whatever reason I cant boot LIVECD from two different ubuntu cds... which perplexes me.  dvd is on 1st boot, yet it doesnt boot ubuntu.

And I guess the USB option is out, is that basically what I understood from your post?

---

### Post by oldfred on 2010-10-07
There seemed to be some work arounds in the threads on bugs.

There is both pendrive and unetbootin.

I would still see why you cannot boot the CD. Was it installed correctly not just a copy of the ISO. Windows software often does it wrong.

Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Allows extra space on flash to be used
[http://rudd-o.com/new-projects/portablelinux](http://rudd-o.com/new-projects/portablelinux)
With lots of links but using FAT, syslinux & grub4dos
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

Has instructions on installing from windows:
Also has links to alternative install -text mode & not liveCD, CD & USB install instructions
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by corcomp84 on 2010-10-07
sometimes pending on the computer you can hit F12 or F11 or F10 to choose your boot device manually.. you could try that... make sure you are using 10.04 as the Ubuntu version because they made some great improvements on the installation process.. I would reinstall the whole thing not just grub..

---

### Post by corcomp84 on 2010-10-07
Did you try just copying the ISO image to the USB drive? it looks like you are using a software to make it.. I have not tried it that way so I am not sure if it will work

---

### Post by PsychedelicWonders on 2010-10-07
> **corcomp84 said:**
> sometimes pending on the computer you can hit F12 or F11 or F10 to choose your boot device manually.. you could try that... make sure you are using 10.04 as the Ubuntu version because they made some great improvements on the installation process.. I would reinstall the whole thing not just grub..

Yeah I was trying to boot it manually via F8 & it still wasnt working?

I'm going to unplug all other HDD's other than 80g Ubuntu & run LIvecd in the dvd again & see what happens.

I really dont want to reinstall the whole thing... I've got hundreds of hours of coding & modifications on my GUI... a lot of bad *** stuff.  I dont remember what version I have but it's only a year old at the latest.

Any other thoughts on how I can fix this?

---

### Post by PsychedelicWonders on 2010-10-07
> **corcomp84 said:**
> Did you try just copying the ISO image to the USB drive? it looks like you are using a software to make it.. I have not tried it that way so I am not sure if it will work

hmm no technically I didnt, I was just following the directions on the Ubuntu download site...

I'll try to drag & drop & see what happens...

---

### Post by PsychedelicWonders on 2010-10-07
Ok I dragged & dropped the iso to the USB and it still gave me the BOOTMGR missing error, even if I pressed F8 to manaually select boot device, USB still gives me BOOTMGR missing error.

I even tried it with just the Ubuntu HDD installed, the other 2 were unplugged and no dice, I was getting an error message about adding bootable media

I tried to F8 manually select dvd with LIVEcd in it & no dice.

I just dont know what to do?

---

### Post by corcomp84 on 2010-10-07
try restoring your default settings in your bios,, I know I have had this problem before

---

### Post by oldfred on 2010-10-07
When you browse the CD, do you see one .iso file or all the files that should be there when it is extracted and copied to the CD?

---

### Post by PsychedelicWonders on 2010-10-07
> **oldfred said:**
> When you browse the CD, do you see one .iso file or all the files that should be there when it is extracted and copied to the CD?

This is what I see:  

And when I try to click on the iso below "files currently on disc" it brings up the windows explorer burn a disk program?

But if its already on there... why's it telling me to burn it again when I click on it?

---

### Post by PsychedelicWonders on 2010-10-07
Ok, so I finally got it to work!

Now I need to fix grub, make a swap partition & add the rest of the unallocated space to the main Ubuntu partition to extend it.

Now I was on this step:

```
sudo mount /dev/sdXY /mnt
```

But this is what happened:

sudo mount /dev/sdXY /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/home
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

What am I doing wrong that it's not mounting?

here is my HDD info:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb142cab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384000+   7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2            9328        9457     1044225    f  W95 Ext'd (LBA)

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc9b241e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953512448    7  HPFS/NTFS
```
I'm trying to mount the 80g HDD.

Thanks.

---

### Post by PsychedelicWonders on 2010-10-07
I just tried to run it again & got this message...

ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/home
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
mount: /dev/sdc1 already mounted or /mnt busy
mount: according to mtab, /dev/sdc1 is already mounted on /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdc
/usr/sbin/grub-setup: error: no signature.
ubuntu@ubuntu:~$ 


What does no signature mean & how do I fix it?

---

### Post by oldfred on 2010-10-07
It is saying it did not find the /boot/grub files in your /mnt to install grub to sdc.

If from liveCD can you look at the sdc1 partition and see if you have /boot and /boot/grub ( not files on liveCD) it may be /media/boot/grub when you click on sdc1 partition.

Sometimes you have to use the full chroot method to install.

HOWTO: Purge and Reinstall Grub 2 from the Live CD -drs305
In cases where the boot info script results look normal, I usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
reinstall & purge of grub.
[http://ubuntuforums.org/showthread.php?t=1350856](http://ubuntuforums.org/showthread.php?t=1350856)

---

### Post by PsychedelicWonders on 2010-10-07
> **oldfred said:**
> It is saying it did not find the /boot/grub files in your /mnt to install grub to sdc.

If from liveCD can you look at the sdc1 partition and see if you have /boot and /boot/grub ( not files on liveCD) it may be /media/boot/grub when you click on sdc1 partition.

Sometimes you have to use the full chroot method to install.

HOWTO: Purge and Reinstall Grub 2 from the Live CD -drs305
In cases where the boot info script results look normal, I usually recommend purging and reinstalling G2 via the LiveCD and chroot. Reinstalling may not recover a failing system if files are missing.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
reinstall & purge of grub.
[http://ubuntuforums.org/showthread.php?t=1350856](http://ubuntuforums.org/showthread.php?t=1350856)

I have it in / I believe correct?

Heres a screenshot:

So you want me to run this Purge option now?

---

### Post by oldfred on 2010-10-08
Your /boot is there, Did you drill down and see grub under /boot?

Yes follow drs305 instructions in the link to chroot into your system and uninstall grub2 (grub-pc) and grub(should not matter but will not hurt)  and reinstall grub2.

---

### Post by PsychedelicWonders on 2010-10-08
> **oldfred said:**
> Your /boot is there, Did you drill down and see grub under /boot?

Yes follow drs305 instructions in the link to chroot into your system and uninstall grub2 (grub-pc) and grub(should not matter but will not hurt)  and reinstall grub2.

Yes I see a grub file within /boot

So I need to basically uninstall whats there & reinstall it?

At what point will I allocate all unused disk space to make the single partition bigger & also create a swap partition?

I'll try that other walk thru now and see what happens...

---

### Post by PsychedelicWonders on 2010-10-08
Ok so I started the purge/install and this is what happened:

```
root@ubuntu:/# /dev/pts /mnt/temp/dev/pts && sudo cp /etc/resolv.conf /mnt/temp/root@ubuntu:/# 
root@ubuntu:/# apt-get update
Get:1 http://ppa.launchpad.net hardy Release.gpg [307B]
Ign http://ppa.launchpad.net hardy/main Translation-en

I SKIPPED A BUNCH OF UPDATE CODE HERE GETTING THE FILES FOR SPACE

Get:30 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [5786B]
Fetched 1841kB in 3s (559kB/s)                         
Reading package lists... Done
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package grub-common
root@ubuntu:/# 



```

So what am I doing wrong

Following that walk through, step 3. The next command will remove *grub*, *grub-pc* (Grub2) and *grub-common*.***** Here is what you will do:
[LIST]
[*]Press ENTER to continue.
[*]Read the warning during the install about removing the bootloader. TAB to highlight "<Yes>" and press ENTER.
[/LIST]
But there wasnt any warning to hit yes to?  The terminal just finished up with the update & sat at a new prompt?

---

### Post by PsychedelicWonders on 2010-10-08
Anyone else?  I tried to run it again & I'm still stuck at this grub-common step #3?

---

### Post by PsychedelicWonders on 2010-10-08
Ok I just tried this route:

```
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# grub-install /dev/sdc
/dev/sdc does not have any corresponding BIOS drive.
root@ubuntu:/# 

```

So how do I fix it so this HDD has a corresponding BIOS drive?

---

### Post by PsychedelicWonders on 2010-10-08
Tried this too:

```
root@ubuntu:/# grub-install /dev/sdc
/dev/sdc does not have any corresponding BIOS drive.
root@ubuntu:/# sudo grub-install --recheck /dev/sdc
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda3: Not found or not a block device.
root@ubuntu:/# 

```

?

---

### Post by PsychedelicWonders on 2010-10-08
Hmm I've been trying a couple of things and came up with this:

```

root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get purge grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package grub-common
root@ubuntu:/# apt-get update
Hit http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US           
Ign http://ppa.launchpad.net hardy Release.gpg                      
Get:1 http://packages.medibuntu.org hardy Release.gpg [197B]         
Ign http://packages.medibuntu.org hardy/free Translation-en_US                                     
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US   
Hit http://us.archive.ubuntu.com hardy Release.gpg                   
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US        
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_US 
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Hit http://ppa.launchpad.net hardy Release                                                 
Get:2 http://packages.medibuntu.org hardy Release [11.7kB]                                                      
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                       
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                         
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US 
Hit http://security.ubuntu.com hardy-security Release                      
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US                             
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                               
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US       
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US     
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US                       
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                                           
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US                              
Hit http://us.archive.ubuntu.com hardy Release                                                   
Hit http://security.ubuntu.com hardy-security/main Packages                                                           
Get:4 http://ppa.launchpad.net hardy Release [27.6kB]                                                                 
Hit http://us.archive.ubuntu.com hardy-updates Release                                                   
Hit http://security.ubuntu.com hardy-security/restricted Packages                         
Hit http://security.ubuntu.com hardy-security/main Sources                                                      
Hit http://security.ubuntu.com hardy-security/restricted Sources                                                
Hit http://security.ubuntu.com hardy-security/universe Packages                                                 
Hit http://ppa.launchpad.net hardy/main Packages                                           
Hit http://ppa.launchpad.net hardy/main Sources                                            
Hit http://packages.medibuntu.org hardy/free Packages                
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/multiverse Packages                                    
Hit http://security.ubuntu.com hardy-security/multiverse Sources                                     
Hit http://us.archive.ubuntu.com hardy/main Packages                                                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages                                           
Hit http://us.archive.ubuntu.com hardy/main Sources                                                  
Hit http://us.archive.ubuntu.com hardy/restricted Sources                                            
Hit http://us.archive.ubuntu.com hardy/universe Packages                                             
Ign http://ppa.launchpad.net hardy/main Packages                               
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://ppa.launchpad.net hardy/main Packages
Fetched 11.9kB in 1s (10.6kB/s)
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package grub-common
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/vmlinuz-2.6.24-21-generic
Found kernel: /boot/vmlinuz-2.6.24-19-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# grub-install /dev/sdc
/dev/sdc does not have any corresponding BIOS drive.
root@ubuntu:/# sudo grub-install --recheck /dev/sdc
Probing devices to guess BIOS drives. This may take a long time.
/dev/sda3: Not found or not a block device.
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
E: Couldn't find package grub-common
root@ubuntu:/# apt-get purge grub grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-pc is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub*
0 upgraded, 0 newly installed, 1 to remove and 195 not upgraded.
After this operation, 1896kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184307 files and directories currently installed.)
Removing grub ...
Purging configuration files for grub ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package grub-common
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  grub-pc
0 upgraded, 1 newly installed, 0 to remove and 195 not upgraded.
Need to get 1041kB of archives.
After this operation, 2859kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com hardy/universe grub-pc 1.96+20080203-1ubuntu2 [1041kB]
Fetched 1041kB in 2s (477kB/s)   
Preconfiguring packages ...
Selecting previously deselected package grub-pc.
(Reading database ... 184261 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.96+20080203-1ubuntu2_amd64.deb) ...
Setting up grub-pc (1.96+20080203-1ubuntu2) ...

root@ubuntu:/# update-grub


^[[A^[[A^[[A^[[B^[[B





```

Right not the terminal still seems to be running the update-grub... but its been taking several minutes already.  Is that normal?

Am I on the right track here?

---

### Post by PsychedelicWonders on 2010-10-08
Now it seems as though it finished update-grub, but then it forced itself into another cycle of it?

```
root@ubuntu:/# update-grub


^[[A^[[A^[[A^[[B^[[B



Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.24-24-generic
Found initrd image: /boot/initrd.img-2.6.24-24-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.24-22-generic
Found initrd image: /boot/initrd.img-2.6.24-22-generic
Found linux image: /boot/vmlinuz-2.6.24-21-generic
Found initrd image: /boot/initrd.img-2.6.24-21-generic
Found linux image: /boot/vmlinuz-2.6.24-19-generic
Found initrd image: /boot/initrd.img-2.6.24-19-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# update-grub


```Once again the cursor has been flashing for roughly 10 minutes in the terminal...

At what point will I know if I've successfully re-installed grub?

---

### Post by PsychedelicWonders on 2010-10-08
Ok I guess I finished it?

This was the last end of it:

```
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# update-grub
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.24-24-generic
Found initrd image: /boot/initrd.img-2.6.24-24-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.24-22-generic
Found initrd image: /boot/initrd.img-2.6.24-22-generic
Found linux image: /boot/vmlinuz-2.6.24-21-generic
Found initrd image: /boot/initrd.img-2.6.24-21-generic
Found linux image: /boot/vmlinuz-2.6.24-19-generic
Found initrd image: /boot/initrd.img-2.6.24-19-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# 
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/temp/dev/pts && sudo umount /mnt/temp/sys && sudo umount /mnt/temp/proc && sudo umount /mnt/temp/dev && sudo umount /dev/sdc1
ubuntu@ubuntu:~$ 

```

So I guess I'm good to go?  I'm going to try to reboot now... not sure if I'm trying to go back to the live cd or into the HDD itself now...

---

### Post by PsychedelicWonders on 2010-10-08
Alright, well after all of that, Ubuntu was not starting.  I even made the 80g HDD the 2nd boot device after dvd & it just gave me the same device media error message

Ideas on what I'm missing & why grub didnt install?

---

### Post by drs305 on 2010-10-08
> **PsychedelicWonders said:**
> Alright, well after all of that, Ubuntu was not starting.  I even made the 80g HDD the 2nd boot device after dvd & it just gave me the same device media error message

Ideas on what I'm missing & why grub didnt install?

Edit: Revised after experimenting with Hardy virtual machine

I see from your repository list that your references are to Hardy. Originally Grub2 wasn't listed in the Hardy repositories and I can't find a listing for "grub-common", which is why it couldn't be installed (grub-common).  See if "grub2" and "grub-pc" are listed as available in Synaptic, and if not try updating the repositories. 

Your options with updated repositories should include reinstalling "grub", installing "grub2" or "grub-pc". "grub2" is a transitional package and you could try installing that to have both grub legacy and grub2 but **just installing "grub-pc**" after purging "grub" should work. 

For Hardy, your best option may first be to just purge/reinstall "grub", which would essentially do the same thing as far as clearing the problem if it's related to boot issues.  If you want to update to grub2, you can follow the purge/install routine, but remove the "grub-common" package from the instructions as it doesn't exist in Hardy.

Optional for the truly bored or desperate:
The version of Grub2 in the Hardy repositories (1.96) is the earliest version. If you really want to try installing grub-pc and can't do so from the Hardy repositories you might be  to grab the grub-pc deb from a later release but I haven't tried installing it that way - there are dependencies on other packages that are probably also unavailable in the Hardy repositories. About the only way would probably be to change your repositories temporarily to karmic, install grub-pc, and then change the repositories back to hardy, but I can't promise it wouldn't break your system. It's something I'd only do on a non-production machine when I had some time and didn't care if I broke it...

---

### Post by PsychedelicWonders on 2010-10-12
> **drs305 said:**
> Edit: Revised after experimenting with Hardy virtual machine

I see from your repository list that your references are to Hardy. Originally Grub2 wasn't listed in the Hardy repositories and I can't find a listing for "grub-common", which is why it couldn't be installed (grub-common).  See if "grub2" and "grub-pc" are listed as available in Synaptic, and if not try updating the repositories. 

Ok bear with me as its been a very long time since I've been on Ubuntu, where do I find Synaptic again & what code do I use to update it?

So you think that could possibly solve the grub booting issue"



> Your options with updated repositories should include reinstalling "grub", installing "grub2" or "grub-pc". "grub2" is a transitional package and you could try installing that to have both grub legacy and grub2 but **just installing "grub-pc**" after purging "grub" should work. 

Ok so when I get this menu for updating the repositories, which one should I pick?  I guess I dont know the difference between them all to pick one?

So you're saying I need to first run your "purge" code again before I update repositories? From this walkthru: [http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

> For Hardy, your best option may first be to just purge/reinstall "grub", which would essentially do the same thing as far as clearing the problem if it's related to boot issues.  If you want to update to grub2, you can follow the purge/install routine, but remove the "grub-common" package from the instructions as it doesn't exist in Hardy.

I dont know the differences between Grub & Grub2... are there any significant ones?  All I can remember from Grub is being given a startup menu to chose which OS I wanted to run - which I enjoyed & prefer to have back.

Thoughts?

Thanks.

---

### Post by PsychedelicWonders on 2010-10-13
Also does should I be setting the 80g ubuntu HDD to boot 2nd after dvd?

Then would it default to the 2nd HDD which is the 500g windows?

---

### Post by oldfred on 2010-10-13
Back in post #2 andrewthomas suggested running the boot info script. I am now lost and I think a lot of the issues of suggesting the wrong version of grub and finding out you have an older Ubuntu and where windows & grub have installed boot loaders would be solved.

Please run boot info script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by PsychedelicWonders on 2010-10-14
> **oldfred said:**
> Back in post #2 andrewthomas suggested running the boot info script. I am now lost and I think a lot of the issues of suggesting the wrong version of grub and finding out you have an older Ubuntu and where windows & grub have installed boot loaders would be solved.

Please run boot info script:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Ok here, you go:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             70   976,768,070   976,768,001   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2         149,838,255   151,926,704     2,088,450   f W95 Ext d (LBA)
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CB653F926B9460                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FE5253A152535E09                       ntfs       JohnnyScience                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        911f7a70-3beb-46c4-ab0f-1a9b73a67a82   ext3                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-24-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-23-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-22-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-21-generic

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Chainload into GRUB 2
root        (hd0,2)
kernel        /boot/grub/core.img

title        Ubuntu 8.04.3 LTS, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd2,1)
if font (hd2,1)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.24-24-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu, linux 2.6.24-24-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu, linux 2.6.24-23-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu, linux 2.6.24-23-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu, linux 2.6.24-22-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu, linux 2.6.24-22-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu, linux 2.6.24-21-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, linux 2.6.24-21-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, linux 2.6.24-19-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu, linux 2.6.24-19-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd2,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/storage ntfs defaults 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  18.7GB: boot/grub/core.img
  18.6GB: boot/grub/grub.cfg
   2.6GB: boot/grub/menu.lst
   9.0GB: boot/grub/stage2
  13.8GB: boot/initrd.img-2.6.24-19-generic
   8.9GB: boot/initrd.img-2.6.24-19-generic.bak
   9.0GB: boot/initrd.img-2.6.24-21-generic
  13.8GB: boot/initrd.img-2.6.24-21-generic.bak
  13.9GB: boot/initrd.img-2.6.24-22-generic
  13.8GB: boot/initrd.img-2.6.24-22-generic.bak
  13.9GB: boot/initrd.img-2.6.24-23-generic
  13.9GB: boot/initrd.img-2.6.24-23-generic.bak
  18.7GB: boot/initrd.img-2.6.24-24-generic
  19.0GB: boot/initrd.img-2.6.24-24-generic.bak
  18.8GB: boot/vmlinuz-2.6.24-19-generic
  13.8GB: boot/vmlinuz-2.6.24-21-generic
  13.8GB: boot/vmlinuz-2.6.24-22-generic
  13.9GB: boot/vmlinuz-2.6.24-23-generic
  17.8GB: boot/vmlinuz-2.6.24-24-generic
  18.7GB: initrd.img
  13.9GB: initrd.img.old
  17.8GB: vmlinuz
  13.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```Ideas on what to do next?

Do I want Grub or Grub2?  Whats the difference?

I'm not sure what version Ubuntu I'm running, something in the 9's I believe, but I do know that I've done a lot of custom coding to make it work & look the way I want it to & I dont want to lose any of it.

---

### Post by PsychedelicWonders on 2010-10-14
Found this:

> Differences between GRUB Legacy and GRUB 2

From the user's view, the biggest difference between the two versions of GRUB concerns the boot menu configuration file. 
GRUB 2:   /boot/grub/grub.cfg
GRUB Legacy:   /boot/grub/menu.lst
The configuration file is used to generate the boot menu you see at boot time.
In GRUB Legacy, you can edit menu.lst directly and in any way you wish.
In GRUB 2, you should not edit grub.cfg directly.  Instead, you edit the file /etc/default/grub (which contains some default settings); this file feeds data to scripts in the folder /etc/grub.d.  And you may edit the scripts (text files) in the folder /etc/grub.d; these scripts are used to generate the configuration file /boot/grub/grub.cfg.  When you need a new grub.cfg, simply do sudo grub-mkconfig -o /boot/grub/grub.cfg.

Yeah I guess I dont really see the difference as I'm not that great of a coder, so I dont care which one I reinstall I guess?

---

### Post by drs305 on 2010-10-14
You don't have Grub installed to any MBR so at boot your system doesn't know where to look for the boot files.

When you tried purging/reinstalling earlier, it gave errors about grub-common. You still have pieces of both Grub and Grub legacy. We can run the commands separately to make sure all the appropriate ones run to completion.

It's a toss up, but I think I'd go with Grub2. It's an early version but should still work properly with your install (you are using Hardy 8.04).

So here are the instructions, to be carried out from a LiveCD:
After you perform the first command, you should probably inspect the contents to ensure you are looking at your Ubuntu install. The third command will open Nautilus so you can see your Ubuntu files. If you don't, just stop and let us know.

Full explanations are in the *chroot* link in my signature line if you need to review them.
```

sudo mkdir /mnt/temp 
sudo mount /dev/sdc1 /mnt/temp  
nautilus /mnt/temp &
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
sudo chroot /mnt/temp

```

You should now be at a root prompt. 

First verify you have an Internet connection by running the 'apt-get update' command, then uninstall grub and grub-pc. If you don't get an Internet connection with the 'update' command, STOP. If you get 'not found' messages on the purge commands that is okay.

```
apt-get update  # Check Internet connection
apt-get purge grub
apt-get purge grub-pc

```

Now install Grub2:
```

apt-get install grub-pc
grub-install /dev/sdc  # Don't include the partition.
update-grub
exit

```

You should now be back at the ubuntu prompt. Unmount and then reboot:
```

for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done

```

Change your BIOS to boot from the sdc drive first.

---

### Post by oldfred on 2010-10-14
You also have an error on your missing swap. fstab is tying to mount an UUID that does not exist and the script shows:

Invalid MBR Signature found Empty Partition

See if gparted will see and correct the missing partition, then find the UUID

sudo blkid

and then edit your fstab from the liveCD in /etc/fstab. I may be mounted as /media/etc/fstab.

---

### Post by PsychedelicWonders on 2010-10-14
> **oldfred said:**
> You also have an error on your missing swap. fstab is tying to mount an UUID that does not exist and the script shows:

Invalid MBR Signature found Empty Partition

See if gparted will see and correct the missing partition, then find the UUID

sudo blkid

and then edit your fstab from the liveCD in /etc/fstab. I may be mounted as /media/etc/fstab.

Ok so you want me to do what exactly in Gparted first before I do what drs305 suggested?

I've pulled it up on the drive I want, C (80g) and its showing 74.53 unallocated... but that cant be right because there is a 20g partition with Ubuntu on it...

Why is it not seeing the partition?

---

### Post by PsychedelicWonders on 2010-10-14
I knew that the Ubuntu partition was still there...

I checked my HDD's with Partition Wizard in Win7 & it came up with this:

So its there.

Now you're saying I need to add a swap partition before I can do the Grub reinstall basically?

Funny thing is I had a swap on there before & it got deleted accidentally just the other day...

---

### Post by oldfred on 2010-10-14
Swap is highly recommended, but you do not have to have one if you have lots of memory. System also seems to work better with swap even with lots of memory and when swap is rarely used. 

The issue may be that you have a swap entry in fstab. Even if you create a new swap its UUID will be different than the UUID in fstab. So you will need to update fstab.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by PsychedelicWonders on 2010-10-19
> **oldfred said:**
> Swap is highly recommended, but you do not have to have one if you have lots of memory. System also seems to work better with swap even with lots of memory and when swap is rarely used. 

The issue may be that you have a swap entry in fstab. Even if you create a new swap its UUID will be different than the UUID in fstab. So you will need to update fstab.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Ok so updating fstab will then see the Ubuntu partition?  I guess I'm confused as to what my next step should be?

---

### Post by oldfred on 2010-10-19
The windows partition manager will not show the linux partitions. You need to use this to see partitions from Ubuntu:
```
sudo fdisk -l
```

This will show your UUIDs.

```
sudo blkid
```

You can use gparted to create a small 1 or 2GB swap if you do not have one and add an entry to fstab.

This was my entry with my UUID:
```
# swap was on /dev/sdc10 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0
```

---

### Post by PsychedelicWonders on 2010-10-19
> **oldfred said:**
> The windows partition manager will not show the linux partitions. You need to use this to see partitions from Ubuntu:
```
sudo fdisk -l
```This will show your UUIDs.

```
sudo blkid
```You can use gparted to create a small 1 or 2GB swap if you do not have one and add an entry to fstab.

This was my entry with my UUID:
```
# swap was on /dev/sdc10 during installation
UUID=09367687-86d1-4fd0-9b81-2787d3196159 none            swap    sw              0       0
```

Ok here is all of that info:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb142cab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384000+   7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc9b241e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953512448    7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2            9328        9457     1044225    f  W95 Ext'd (LBA)
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="01CB653F926B9460" TYPE="ntfs" 
/dev/sdb1: LABEL="JohnnyScience" UUID="FE5253A152535E09" TYPE="ntfs" 
/dev/sdc1: UUID="911f7a70-3beb-46c4-ab0f-1a9b73a67a82" SEC_TYPE="ext2" TYPE="ext3" 
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```I tried to create a SWAP partition with gparted, but it told me in order to create a new partition I would have to create a new Partition table & when I tried to do that it gave me a warning that it was about to erase ALL data on the HDD - which I dont want to do as I'll lose my Ubuntu Partition.

I can always add the swap later, I'd rather get Grub setup for now.

So what are my next steps now in order to reinstall Grub/Grub2?

---

### Post by oldfred on 2010-10-19
I do not see anything wrong with sdc. You seem to have some error in sdb flags that it says a write will correct. But if gparted will not see the partitions then either gparted has an issue or the partition does.

To see if you have errors in sdc1
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdc1
if errors:
sudo e2fsck -f -y -v /dev/sdc1

If grub2 also does not see drive correctly it likely will not install. I would install it to sdc and set sdc as the boot drive in BIOS.

Install MBR from LiveCD, Ubuntu install on sdc1 and want grub2 in drive sda's MBR:
Find linux partition, change sdc1 if not correct, and/or even sdc if sda wanted:
sudo fdisk -l
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

If you have run the checks and the above short method to reinstall grub2 does not work, use the full chroot method here:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by PsychedelicWonders on 2010-10-20
> **oldfred said:**
> I do not see anything wrong with sdc. You seem to have some error in sdb flags that it says a write will correct. But if gparted will not see the partitions then either gparted has an issue or the partition does.

To see if you have errors in sdc1
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdc1
if errors:
sudo e2fsck -f -y -v /dev/sdc1

If grub2 also does not see drive correctly it likely will not install. I would install it to sdc and set sdc as the boot drive in BIOS.

Install MBR from LiveCD, Ubuntu install on sdc1 and want grub2 in drive sda's MBR:
Find linux partition, change sdc1 if not correct, and/or even sdc if sda wanted:
sudo fdisk -l
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdc


Ok, is the reason gparted wasnt seeing my Ubuntu partition because I didnt have the drive mounted to start perhaps?

So I'll run these codes to start:

```
sudo e2fsck -C0 -p -f -v /dev/sdc1
if errors:
sudo e2fsck -f -y -v /dev/sdc1
```

But then I'm not sure what to do when you're talking about installing the MBR - I dont want to change from sdc to sda if I dont have to...

```
sudo fdisk -l
sudo mount /dev/sdc1 /mnt
sudo grub-install /mnt/ /dev/sdc
``` - I think that is my root directory, how can I be sure?  

Sorry once again its been quite a while since I've been on Ubuntu.

---

### Post by drs305 on 2010-10-20
> **PsychedelicWonders said:**
> Ok, is the reason gparted wasnt seeing my Ubuntu partition because I didnt have the drive mounted to start perhaps?

GParted will see partitions whether they are mounted or not.


> 
But then I'm not sure what to do when you're talking about installing the MBR - I dont want to change from sdc to sda if I dont have to...

```
sudo fdisk -l
sudo mount /dev/sdc1 /mnt
sudo grub-install /mnt/ /dev/sdc
``` - I think that is my root directory, how can I be sure?  


If the partitions are still mounted as they were when you ran the boot info script, the only Linux partition you have is sdc1, so you can't really install it to the wrong partition.

Your command is a bit off though. Here is how you should run the command, assuming you are using a LiveCD:
```

sudo mount /dev/sdc1 /mnt/
sudo grub-install --root-directory=/mnt /dev/sdc
```

You will want your computer to boot to sdc, so change it in the system's BIOS.

---

### Post by PsychedelicWonders on 2010-10-20
Ok so I made some progress, but stuck on the install of GRUB, see at the bottom:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdc1

                                                                               
  215957 inodes used (16.79%)
    4460 non-contiguous files (2.1%)
     260 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 11154/862/0
 4497957 blocks used (87.84%)
       0 bad blocks
       1 large file

  167761 regular files
   24789 directories
      69 character device files
      26 block device files
       2 fifos
     470 links
   23293 symbolic links (21191 fast symbolic links)
       8 sockets
--------
  216418 files
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb142cab0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488384000+   7  HPFS/NTFS

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc9b241e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953512448    7  HPFS/NTFS
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2            9328        9457     1044225    f  W95 Ext'd (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo grub-install /mnt/ /dev/sdc
More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --root-directory=DIR    install GRUB images under the directory DIR
                          instead of the root directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use

INSTALL_DEVICE can be a GRUB device name or a system device filename.

grub-install copies GRUB images into /boot/grub (or /grub on NetBSD and
OpenBSD), and uses grub-setup to install grub into the boot sector.

If the --root-directory option is used, then grub-install will copy
images into the operating system installation rooted at that directory.

Report bugs to <bug-grub@gnu.org>.
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdc
/usr/sbin/grub-setup: error: no signature.
ubuntu@ubuntu:~$ 


```What do I need to do?

Am I supposed to be replacing the words "root-directory" with something else?  I believe my root is / like "normal" ?

---

### Post by drs305 on 2010-10-20
The way you ran the command the second time, with "--root-directory=/mnt/" was correct.

I've been away from this thread for a while. Are you still using Hardy, and did you ever get around to installing Grub 2 per Post # 48? I don't think the command will work if you don't have Grub2.

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> I've been away from this thread for a while. Are you still using Hardy, and did you ever get around to installing Grub 2 per Post # 48?

I'm using the LiveCD of 10.04 I think to try and install grub for my Hardy system.

It's still not installed yet.

I thought I did everything you & oldfred just told me to do?

So I now need to run back through post #48?

Why didnt it install when I just tried but gave me an error instead:

```
sudo fdisk -l
sudo mount /dev/sdc1 /mnt
sudo grub-install /mnt/ /dev/sdc
```

---

### Post by drs305 on 2010-10-20
"grub-install", even though it sounds like the correct command, only writes to the MBR and puts some files into /boot/grub. The actual command to install Grub 2 is "apt-get install grub-pc". You can't run it directly from the LiveCD - you have to chroot per Post #48.

Added since we cross-posted:
> Why didnt it install when I just tried but gave me an error instead:

```
sudo mount /dev/sdc1 /mnt
sudo grub-install /mnt/ /dev/sdc
```

Explained above, but the command you typed in the quote is not one we gave you. Either copy/paste the commands or double check them to make sure they are *exactly* as posted.

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> "grub-install", even though it sounds like the correct command, only writes to the MBR and puts some files into /boot/grub. The actual command to install Grub 2 is "apt-get install grub-pc". You can't run it directly from the LiveCD - you have to chroot per Post #48.

Ahh ok, I will try to do #48 again right now & post back with results in a few minutes.

Please stay tuned.

Thanks.

---

### Post by PsychedelicWonders on 2010-10-20
Ok here are the results of going through #48 so far to installing grub-pc as it has been doing so for several minutes already.

So I should be on the right track now right?

I plan to run the rest of the code in #48, but wanted to post my progress now since installing grub-pc seems to be taking a while...

```

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mkdir /mnt/temp 
ubuntu@ubuntu:~$ sudo mount /dev/sdc1 /mnt/temp  
ubuntu@ubuntu:~$ nautilus /mnt/temp &
[1] 4970
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
[1]+  Done                    nautilus /mnt/temp
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update 
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US       
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US 
Hit http://ppa.launchpad.net hardy Release.gpg                                             
Ign http://ppa.launchpad.net hardy/main Translation-en_US                                  
Ign http://ppa.launchpad.net hardy Release.gpg                       
Get:1 http://security.ubuntu.com hardy-security Release.gpg [198B]   
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                          
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US    
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US  
Get:2 http://us.archive.ubuntu.com hardy-updates Release.gpg [198B]  
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US                              
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US                
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US                  
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US                
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Ign http://ppa.launchpad.net hardy Release.gpg                       
Ign http://ppa.launchpad.net hardy/main Translation-en_US            
Hit http://ppa.launchpad.net hardy Release                                                 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                                      
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                                        
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US                
Get:3 http://security.ubuntu.com hardy-security Release [58.5kB]                          
Hit http://us.archive.ubuntu.com hardy Release                                                                      
Get:4 http://ppa.launchpad.net hardy Release [27.6kB]                                                               
Get:5 http://ppa.launchpad.net hardy Release [27.6kB]                                            
Get:6 http://us.archive.ubuntu.com hardy-updates Release [58.5kB]                                         
Hit http://ppa.launchpad.net hardy/main Packages                                                       
Hit http://ppa.launchpad.net hardy/main Sources                                                        
Get:7 http://packages.medibuntu.org hardy Release.gpg [197B]                                            
Ign http://packages.medibuntu.org hardy/free Translation-en_US                                                   
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US                 
Ign http://ppa.launchpad.net hardy/main Packages                                   
Get:8 http://packages.medibuntu.org hardy Release [11.7kB]                         
Ign http://ppa.launchpad.net hardy/main Packages                                                              
Get:9 http://security.ubuntu.com hardy-security/main Packages [277kB]                             
Hit http://ppa.launchpad.net hardy/main Packages                                                
Hit http://us.archive.ubuntu.com hardy/main Packages                                            
Hit http://us.archive.ubuntu.com hardy/restricted Packages                 
Hit http://us.archive.ubuntu.com hardy/main Sources                        
Hit http://us.archive.ubuntu.com hardy/restricted Sources                                        
Hit http://us.archive.ubuntu.com hardy/universe Packages                                         
Hit http://us.archive.ubuntu.com hardy/universe Sources                    
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                 
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                  
Get:10 http://packages.medibuntu.org hardy/free Packages [6344B]           
Hit http://ppa.launchpad.net hardy/main Packages                                                                       
Get:11 http://us.archive.ubuntu.com hardy-updates/main Packages [499kB]                          
Get:12 http://packages.medibuntu.org hardy/non-free Packages [6112B]              
Get:13 http://us.archive.ubuntu.com hardy-updates/restricted Packages [10.3kB]            
Get:14 http://us.archive.ubuntu.com hardy-updates/main Sources [187kB]       
Get:15 http://security.ubuntu.com hardy-security/restricted Packages [10.3kB]
Get:16 http://security.ubuntu.com hardy-security/main Sources [112kB]                     
Get:17 http://us.archive.ubuntu.com hardy-updates/restricted Sources [944B]      
Get:18 http://us.archive.ubuntu.com hardy-updates/universe Packages [247kB] 
Get:19 http://us.archive.ubuntu.com hardy-updates/universe Sources [62.9kB]        
Get:20 http://security.ubuntu.com hardy-security/restricted Sources [935B]       
Get:21 http://security.ubuntu.com hardy-security/universe Packages [131kB]             
Get:22 http://us.archive.ubuntu.com hardy-updates/multiverse Packages [28.9kB]          
Get:23 http://us.archive.ubuntu.com hardy-updates/multiverse Sources [5786B]     
Get:24 http://security.ubuntu.com hardy-security/universe Sources [28.3kB]       
Get:25 http://security.ubuntu.com hardy-security/multiverse Packages [14.5kB]
Get:26 http://security.ubuntu.com hardy-security/multiverse Sources [1825B]
Fetched 1760kB in 4s (434kB/s)                        
Reading package lists... Done
root@ubuntu:/# apt-get purge grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 195 not upgraded.
root@ubuntu:/# apt-get purge grub-p
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package grub-p
root@ubuntu:/# apt-get purge grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-pc*
0 upgraded, 0 newly installed, 1 to remove and 195 not upgraded.
After this operation, 2859kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 184377 files and directories currently installed.)
Removing grub-pc ...
Saving menu.lst backup in /boot/grub/menu.lst_backup_by_grub2_prerm
Running update-grub Legacy to remove our core.img in it
    Searching for GRUB installation directory ... found: /boot/grub
    Searching for default file ... found: /boot/grub/default
    Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
    Searching for splash image ... none found, skipping ...
    Found kernel: /boot/vmlinuz-2.6.24-24-generic
    Found kernel: /boot/vmlinuz-2.6.24-23-generic
    Found kernel: /boot/vmlinuz-2.6.24-22-generic
    Found kernel: /boot/vmlinuz-2.6.24-21-generic
    Found kernel: /boot/vmlinuz-2.6.24-19-generic
    Found kernel: /boot/memtest86+.bin
    Updating /boot/grub/menu.lst ... done
    
Purging configuration files for grub-pc ...
root@ubuntu:/# apt-get install grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 libglitz-glx1 libglitz1 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  desktop-base
The following NEW packages will be installed:
  grub-pc
0 upgraded, 1 newly installed, 0 to remove and 195 not upgraded.
Need to get 0B/1041kB of archives.
After this operation, 2859kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-pc.
(Reading database ... 184261 files and directories currently installed.)
Unpacking grub-pc (from .../grub-pc_1.96+20080203-1ubuntu2_amd64.deb) ...
Setting up grub-pc (1.96+20080203-1ubuntu2) ...


```

---

### Post by drs305 on 2010-10-20
Yes, it looks like it is progressing normally. There will be a delay while the system builds the new initrd.img, which takes a few moments.

But please be patient, we're not on IRC...  ;-)

---

### Post by PsychedelicWonders on 2010-10-20
Ok here is the rest of it... I guess I'm good now right?

It should boot up to my old Ubuntu now finally?

```
Setting up grub-pc (1.96+20080203-1ubuntu2) ...
Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.24-24-generic
Found initrd image: /boot/initrd.img-2.6.24-24-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.24-22-generic
Found initrd image: /boot/initrd.img-2.6.24-22-generic
Found linux image: /boot/vmlinuz-2.6.24-21-generic
Found initrd image: /boot/initrd.img-2.6.24-21-generic
Found linux image: /boot/vmlinuz-2.6.24-19-generic
Found initrd image: /boot/initrd.img-2.6.24-19-generic
Found memtest86+ image: /boot/memtest86+.bin
done

root@ubuntu:/# update-grub

Updating /boot/grub/grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.24-24-generic
Found initrd image: /boot/initrd.img-2.6.24-24-generic
Found linux image: /boot/vmlinuz-2.6.24-23-generic
Found initrd image: /boot/initrd.img-2.6.24-23-generic
Found linux image: /boot/vmlinuz-2.6.24-22-generic
Found initrd image: /boot/initrd.img-2.6.24-22-generic
Found linux image: /boot/vmlinuz-2.6.24-21-generic
Found initrd image: /boot/initrd.img-2.6.24-21-generic
Found linux image: /boot/vmlinuz-2.6.24-19-generic
Found initrd image: /boot/initrd.img-2.6.24-19-generic
Found memtest86+ image: /boot/memtest86+.bin
done
root@ubuntu:/# 
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys / ; do sudo umount /mnt/temp$i ; done
ubuntu@ubuntu:~$ 

```

---

### Post by drs305 on 2010-10-20
> **PsychedelicWonders said:**
> Ok here is the rest of it... I guess I'm good now right?

It should boot up to my old Ubuntu now finally?

I'm not so sure. We are only up to post #67.  :guitar:

As long as BIOS boots to sdc...

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> I'm not so sure. We are only up to post #67.  :guitar:

As long as BIOS boots to sdc...

Ok after all of that (which seemed successful correct?)

After rebooting I still received this error:

Reboot & select proper boot device or insert boot media in selected boot device and press a key...

---

### Post by drs305 on 2010-10-20
> **PsychedelicWonders said:**
> Reboot & select proper boot device or insert boot media in selected boot device and press a key...

Is that a BIOS message? Did you go into BIOS and select the correct drive?
Does BIOS show that drive?

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> Is that a BIOS message? Did you go into BIOS and select the correct drive?
Does BIOS show that drive?

Yes I receive that in bios and yes bios sees the drive correctly.  I even tried to run BBS via F8 to force it to chose that drive & still the same error?

---

### Post by drs305 on 2010-10-20
I am not a BIOS or drive expert. Perhaps *oldfred* will be able to help out. It's probably time to run another boot info script to see what your current system situation is...

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> I am not a BIOS or drive expert. Perhaps *oldfred* will be able to help out. It's probably time to run another boot info script to see what your current system situation is...

Ok, whats the code for that so I can run it now for you guys?

---

### Post by drs305 on 2010-10-20
> **PsychedelicWonders said:**
> Ok, whats the code for that so I can run it now for you guys?

If you are running the LiveCd and downloaded the script to your Desktop:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> If you are running the LiveCd and downloaded the script to your Desktop:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

Ok you're saying this script right?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I'll do that now & post results...

---

### Post by drs305 on 2010-10-20
Last entry from me in this thread. We are at post #75 and back to post #1. :-(

When you installed the new hard drive, did you change BIOS settings to SATA, perhaps with AHCI? Is your old drive IDE? You may need to change the BIOS settings back to allow it to recognize your old drive or allow it to boot. But as I said before, I have little knowledge about problems I haven't personally experienced.

My recommendation at this point would be to use part of your new 500GB drive for Ubuntu.

Best of luck.

---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> Last entry from me in this thread. We are at post #75 and back to post #1. :-(

When you installed the new hard drive, did you change BIOS settings to SATA, perhaps with AHCI? Is your old drive IDE? You may need to change the BIOS settings back to allow it to recognize your old drive or allow it to boot. But as I said before, I have little knowledge about problems I haven't personally experienced.

My recommendation at this point would be to use part of your new 500GB drive for Ubuntu.

Best of luck.

Yeah we're back to square one and I dont understand why after all this time grub hasnt been installed as I followed directions to a T.

And all drives are SATA and technically all I did was add a new media drive (which is perfect fine and not an issue)

But for some reason I still cant access the Ubuntu partition I had before I installed Windows 7 and it wrote over grub.

This really should have been simpiler than it was & even though I didnt know exactly what code to use, as I mentioned, I followed all walk-thrus to a T.

And I'm still no further than when I started this.

The Ubuntu Partition IS there and I can see it Wizard Partition in Windows, so I dont understand why Ubuntu isnt seeing it and only 74 of unallocated space.

Here are the results of boot script:

```

Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.3 LTS
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             70   976,768,070   976,768,001   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2         149,838,255   151,926,704     2,088,450   f W95 Ext d (LBA)
Invalid MBR Signature found
Empty Partition


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        01CB653F926B9460                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FE5253A152535E09                       ntfs       JohnnyScience                 
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        911f7a70-3beb-46c4-ab0f-1a9b73a67a82   ext3                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdc1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title        Debian GNU/Linux, kernel 2.6.24-24-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-24-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-23-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-23-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-23-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-22-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-22-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-22-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-22-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-21-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-21-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-21-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-21-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-19-generic
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
savedefault

title        Debian GNU/Linux, kernel 2.6.24-19-generic (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
initrd        /boot/initrd.img-2.6.24-19-generic
savedefault

title        Debian GNU/Linux, kernel memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=========================== sdc1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/update-grub using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
set default=0
set timeout=5
set root=(hd2,1)
if font (hd2,1)/usr/share/grub/unicode.pff ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  terminal gfxterm
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_hurd ###
### END /etc/grub.d/10_hurd ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, linux 2.6.24-24-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu, linux 2.6.24-24-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-24-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-24-generic
}
menuentry "Ubuntu, linux 2.6.24-23-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu, linux 2.6.24-23-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-23-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-23-generic
}
menuentry "Ubuntu, linux 2.6.24-22-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu, linux 2.6.24-22-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-22-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-22-generic
}
menuentry "Ubuntu, linux 2.6.24-21-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, linux 2.6.24-21-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-21-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-21-generic
}
menuentry "Ubuntu, linux 2.6.24-19-generic" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro quiet splash
    initrd    (hd2,1)/boot/initrd.img-2.6.24-19-generic
}
menuentry "Ubuntu, linux 2.6.24-19-generic (single-user mode)" {
    linux    (hd2,1)/boot/vmlinuz-2.6.24-19-generic root=UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 ro single
    initrd    (hd2,1)/boot/initrd.img-2.6.24-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux    (hd2,1)/boot/memtest86+.bin
}
### END /etc/grub.d/20_memtest86+ ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/storage ntfs defaults 0 0

=================== sdc1: Location of files loaded by Grub: ===================


  18.7GB: boot/grub/core.img
  18.6GB: boot/grub/grub.cfg
   2.6GB: boot/grub/menu.lst
   9.0GB: boot/grub/stage2
  13.8GB: boot/initrd.img-2.6.24-19-generic
   8.9GB: boot/initrd.img-2.6.24-19-generic.bak
   9.0GB: boot/initrd.img-2.6.24-21-generic
  13.8GB: boot/initrd.img-2.6.24-21-generic.bak
  13.9GB: boot/initrd.img-2.6.24-22-generic
  13.8GB: boot/initrd.img-2.6.24-22-generic.bak
  13.9GB: boot/initrd.img-2.6.24-23-generic
  13.9GB: boot/initrd.img-2.6.24-23-generic.bak
  18.7GB: boot/initrd.img-2.6.24-24-generic
  19.0GB: boot/initrd.img-2.6.24-24-generic.bak
  18.8GB: boot/vmlinuz-2.6.24-19-generic
  13.8GB: boot/vmlinuz-2.6.24-21-generic
  13.8GB: boot/vmlinuz-2.6.24-22-generic
  13.9GB: boot/vmlinuz-2.6.24-23-generic
  17.8GB: boot/vmlinuz-2.6.24-24-generic
  18.7GB: initrd.img
  13.9GB: initrd.img.old
  17.8GB: vmlinuz
  13.9GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by drs305 on 2010-10-20
This is the problem: 

> 
Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    40,965,749    40,965,687  83 Linux
/dev/sdc2         149,838,255   151,926,704     2,088,450   f W95 Ext d (LBA)
[COLOR="Red"]Invalid MBR Signature found
Empty Partition
[/COLOR]


---

### Post by PsychedelicWonders on 2010-10-20
> **drs305 said:**
> This is the problem:

But I re-installed the MBR the way Oldfred told me to?  And shouldnt it have re-written it when I installed grub this last time?

And there is a partition on the HDD, windows see it based on the pic in my last post, so why isnt ubuntu?

---

### Post by drs305 on 2010-10-20
Can anything write to the MBR?

Is there a BIOS setting locking writing to the MBR?
Do you have a Windows app (Norton Go Back, etc) that may have prevented writing to the MBR?

From the LiveCD, install testdisk and lilo
```
sudo apt-get testdisk lilo
```

Try installing lilo, then run the bootinfo  script and see if it says lilo is installed in the MBR of sdc. Disregard the lilo messages about installation:
```
sudo lilo -M /dev/sdc mbr
```

If not successful, try writing testdisk to the MBR just to see if anything will write to it:
```
sudo testdisk /dev/sdc
```
Proceed > Intel > MBR Code > Y > Y
See if it wrote to the MBR by running bootinfo. Note this will remove any bootloaders on the drive and you will have to (re)install them.

TestDisk can also analyse and repair partitions, but I'm not about to get into that. Search for testdisk and 'step by step'.

---

### Post by oldfred on 2010-10-20
The issue is not installing grub or grub2 nor creating the swap as all these are failing because of a bad partition table in the MBR. Not sure what you did when you removed windows from this drive but the partition table is corrupted. At this point I would suggest total reinstall. 

The only other possibility which I do not know too much about is to use testdisk to see if it can repair the partition table.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

