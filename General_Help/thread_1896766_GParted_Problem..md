---
title: "GParted Problem."
date: 2011-12-17
forum: General Help
---

### Post by AaronDaycentChild on 2011-12-17
I'm having trouble re-sizing partitions with GParted. It doesn't seem to allow me to "Resize or Move" it:

[IMG]http://img833.imageshack.us/img833/4159/screenshotat20111217231.png[/IMG]

This is what shows up; some of the options aren't highlighted so I can't select them. I also tried unmounting the drive (/dev/sda1) but an error message just pops up telling me I should unmount manually..

Does anyone know why this might be happening?

---

### Post by cioma on 2011-12-17
In order to resize you have to unmount, but you can't unmount root filesystem.
Create Ubuntu LiveCD/LiveUSB, boot from it and start GParted from it.

---

### Post by MG&amp;TL on 2011-12-17
Is this the hard disk you are currently booting off? In which case, you can't.

my suggestion would be:

a) Don't. Don't resize the partitions, let a distribution installer do it. That handles bootloaders, MBRs, and all the other nasty stuff that isn't pleasant to fail on you.

b) If you do need to, boot ubuntu off a stick (or disk), then use gparted from there, you won't have mounted the disk then. Select "try ubuntu", then  look for gparted.

---

### Post by AaronDaycentChild on 2011-12-17
> **cioma said:**
> In order to resize you have to unmount, but you can't unmount root filesystem.
Create Ubuntu LiveCD/LiveUSB, boot from it and start GParted from it.

Ah yes, of course. Thank you, I will do that.

> **MG&TL said:**
> Is this the hard disk you are currently booting off? In which case, you can't.

my suggestion would be:

a) Don't. Don't resize the partitions, let a distribution installer do it. That handles bootloaders, MBRs, and all the other nasty stuff that isn't pleasant to fail on you.

b) If you do need to, boot ubuntu off a stick (or disk), then use gparted from there, you won't have mounted the disk then. Select "try ubuntu", then  look for gparted.

Yeah, I need windows 7, so I need to format the unallocated space for it. 
Is there a high risk of this going completely backward and destroying my drive? because I DO NOT want to go through that again..

---

### Post by oldfred on 2011-12-17
You will need a primary NTFS partition with the boot flag (manage flags). If partition is created in advance Windows 7 will only use one partition. If you let windows create partitions it has been known to do some odd things with extended partitions, beyond end of drive.

You also need liveCD to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")


If dual booting you may want another NTFS partition just for shared data. You then can make the Windows 7 system partition smaller.

---

### Post by worksofcraft on 2011-12-17
> **MG&TL said:**
> 
my suggestion would be:

a) Don't. Don't resize the partitions, let a distribution installer do it. That handles bootloaders, MBRs, and all the other nasty stuff that isn't pleasant to fail on you.


I totally agree with this. You will get nothing but problems.

My suggestion is that you buy a second hard drive and install windows on that.

Just to be on the safe side, unplug your Ubuntu drive SATA cable while you let Windows do it's thing.

Then you can plug it back in and run update-grub, or is that gryb-mkconfig or update-grub2 these days...

If you want your Windows disk to be able to boot without the Ubuntu disk then you should force grub boot loader just to be on the Ubuntu disk and not plastered all over all the other ones... then you can simply pop the disk boot priorities in your BIOS instead of crossing your fingers and praying every time you do an update.

---

### Post by AaronDaycentChild on 2011-12-18
> **oldfred said:**
> You will need a primary NTFS partition with the boot flag (manage flags). If partition is created in advance Windows 7 will only use one partition. If you let windows create partitions it has been known to do some odd things with extended partitions, beyond end of drive.

You also need liveCD to reinstall grub2's boot loader to the MBR.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")


If dual booting you may want another NTFS partition just for shared data. You then can make the Windows 7 system partition smaller.

Thank you! This was very helpful.

> **worksofcraft said:**
> I totally agree with this. You will get nothing but problems.

My suggestion is that you buy a second hard drive and install windows on that.

Just to be on the safe side, unplug your Ubuntu drive SATA cable while you let Windows do it's thing.

Then you can plug it back in and run update-grub, or is that gryb-mkconfig or update-grub2 these days...

If you want your Windows disk to be able to boot without the Ubuntu disk then you should force grub boot loader just to be on the Ubuntu disk and not plastered all over all the other ones... then you can simply pop the disk boot priorities in your BIOS instead of crossing your fingers and praying every time you do an update.

Damn, now I'm really apprehensive about going through with it. 
Unfortunately,I do not have enough cash for another hard drive. I need to dual boot. 

So if I were to create a new partition, install windows on the new partition and then re-install Grub 2 so I can dual boot, it would give me loads of problems?

---

### Post by oldfred on 2011-12-18
A second hard drive is always the best way, but many dual boot with one drive without issue.

Some have issues as they run some proprietary Windows software that has DRM (may write some hidden data on drive that interferes with grub), or aggressive virus checking software that thinks grub is a virus in the MBR.

Do not directly write into the Windows system partition from Ubuntu (read is find, or if making repairs it may be necessary), use the shared NTFS data partition. Do not hibernate in Windows and then write anything in NTFS as then the hiberfile will be corrupted. Mostly common sense of keeping dual boot separate.

---

### Post by xyzzyman on 2011-12-18
I installed Windows 7 after installing Ubuntu & Arch. You'll want Windows on a primary partition, not in your extended. Your shared NTFS partition can be in the extended no problems. Your best bet is to follow these steps:

1.) Install Bleachbit in Ubuntu. Run it as each user and as root. Cleans up lots of temp & cache files (Just helps speed up resizing.). Now is a good time to do a backup of important files. You have >100GB's on your Ubuntu partition so hopefully you have an external. 
2.) Boot into recovery mode option from the grub menu, and choose the 'fsck check file systems' option.
3.) Boot ubuntu live or the latest gparted live. Don't mount your drives, just go and resize your sda1 partition down to where you want it. Apply.
5.) Create an NTFS partition to the size you want right after sda1. Remember that a default windows 7 install is 10-15GB's alone. I use 30GB for mine but adjust accordingly. It's going to probably be created as sda3. Apply.
6.) Resize the extended partition to fill the space that's left. Apply.
7.) Create an NTFS partition in the extended, and give it a name such as Storage. You can also label your Windows partition if you like. Just looks cleaner in Nautilus. Apply.
8.) Install Windows.
9.) Once it's done all it's reboot and it's set, load your Ubuntu Live CD and install/run boot-repair.

```
suodo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```

That'll reinstall your grub2 for you and list windows for you.

10.) Back in Ubuntu I'd recommend editing your /etc/fstab to auto-mount the Shared partition, and leaving the Windows one alone. You can always manually mount if need be, but better to just leave it out of site. My fstab for example:

```
# / was on /dev/sda1 during installation
UUID=7a1fc3ea-2319-476a-9298-2dbda12e1f6f   /                    ext4     defaults,noatime,errors=remount-ro                               0  1  

# /home was on /dev/sda5 during installation
UUID=05a095a6-88a0-4d31-8737-49902392e831   /home                ext4     noatime,nodiratime                                               0  2  


#/dev/sda6 Storage
UUID=53557F2330DBC621                       /media/Storage       ntfs  default,noatime,nodiratime                            0  0  

#/dev/sda8 VirtualMachines
UUID=185AEA565FA0300B                                    /media/VirtualMachines               ntfs     defaults,noatime,nodiratime                    0  0  

#/dev/sda7 Swap
UUID=83c0bbf6-8c94-480e-8c12-17b6788940ad   none                 swap     sw                                                               0  0  
```

I recommend using the UUID's instead of /dev/sdX as I have had sda #'s change on me. I had a # of 10GB partition in my extended when I installed Windows to /dev/sda4 (My extended was sda3), and when I rebooted into Ubuntu, they were all renumbered (sda4 became sda3, then everything in the extended which was now sda4 became sequential, as you can see that is no longer the case)

---

### Post by larrypg on 2011-12-18
Hello,

Although I have limited knowledge I think I can see a few problems (and a few questions) if you wanted to install Win 7 to the unallocated space.  Most of the problems associated with this have already been mentioned but it is sort of hard to see exactly how your HD is set up with the thing in the middle.  

If you notice the size of your unallocated space you will see that it is just a tiny slice of the drive.  If you want to also run Win 7 and programs then you need to allocate more of the drive to it. 

Although it is a bit hard to tell exactly, right now you seem to have a 454 Gib / partition which is probably about 10 times bigger than it needs to be.  I am thinking that if you want to run Win 7 and programs you will need around 60 Gib for it. 



This part is where my limited knowledge comes in... I think, although I am not sure, that Win 7 sort of likes to be at the start of the disc.  You would have to move everything to the right to make an unallocated space at the beginning of the disc which can cause a few problems.   

This is just a question but I thought that an extended partition was just a vessel to put logical partitions in but there seems to be a boot flag on the extended itself.  

I sure hope you either have a backup in place or you do not mind erasing the drive but it seems that it would be easier to first install Win 7 and then install Ubuntu. Depending on which you will be using more will determine the amount of space you give it.  

I have a bit more to say but just previewed the post and I am sure long winded.

---

### Post by xyzzyman on 2011-12-18
Larry, 

He is resizing the Ubuntu partition to make that space for the NTFS partition. He just was trying to do it while the drive was mounted which was the problem.

---

### Post by larrypg on 2011-12-18
Hello,

This was the line that I was a bit concerned about..."Yeah, I need windows 7, so I need to format the unallocated space for it." which by the screen shot is just a very tiny partition.

---

### Post by AaronDaycentChild on 2011-12-20
> **oldfred said:**
> A second hard drive is always the best way, but many dual boot with one drive without issue.

Some have issues as they run some proprietary Windows software that has DRM (may write some hidden data on drive that interferes with grub), or aggressive virus checking software that thinks grub is a virus in the MBR.

Do not directly write into the Windows system partition from Ubuntu (read is find, or if making repairs it may be necessary), use the shared NTFS data partition. Do not hibernate in Windows and then write anything in NTFS as then the hiberfile will be corrupted. Mostly common sense of keeping dual boot separate.

Thank you! I will remember that.

> **xyzzyman said:**
> I installed Windows 7 after installing Ubuntu & Arch. You'll want Windows on a primary partition, not in your extended. Your shared NTFS partition can be in the extended no problems. Your best bet is to follow these steps:

1.) Install Bleachbit in Ubuntu. Run it as each user and as root. Cleans up lots of temp & cache files (Just helps speed up resizing.). Now is a good time to do a backup of important files. You have >100GB's on your Ubuntu partition so hopefully you have an external. 
2.) Boot into recovery mode option from the grub menu, and choose the 'fsck check file systems' option.
3.) Boot ubuntu live or the latest gparted live. Don't mount your drives, just go and resize your sda1 partition down to where you want it. Apply.
5.) Create an NTFS partition to the size you want right after sda1. Remember that a default windows 7 install is 10-15GB's alone. I use 30GB for mine but adjust accordingly. It's going to probably be created as sda3. Apply.
6.) Resize the extended partition to fill the space that's left. Apply.
7.) Create an NTFS partition in the extended, and give it a name such as Storage. You can also label your Windows partition if you like. Just looks cleaner in Nautilus. Apply.
8.) Install Windows.
9.) Once it's done all it's reboot and it's set, load your Ubuntu Live CD and install/run boot-repair.

```
suodo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update && sudo apt-get install -y boot-repair && boot-repair
```

That'll reinstall your grub2 for you and list windows for you.

10.) Back in Ubuntu I'd recommend editing your /etc/fstab to auto-mount the Shared partition, and leaving the Windows one alone. You can always manually mount if need be, but better to just leave it out of site. My fstab for example:

```
# / was on /dev/sda1 during installation
UUID=7a1fc3ea-2319-476a-9298-2dbda12e1f6f   /                    ext4     defaults,noatime,errors=remount-ro                               0  1  

# /home was on /dev/sda5 during installation
UUID=05a095a6-88a0-4d31-8737-49902392e831   /home                ext4     noatime,nodiratime                                               0  2  


#/dev/sda6 Storage
UUID=53557F2330DBC621                       /media/Storage       ntfs  default,noatime,nodiratime                            0  0  

#/dev/sda8 VirtualMachines
UUID=185AEA565FA0300B                                    /media/VirtualMachines               ntfs     defaults,noatime,nodiratime                    0  0  

#/dev/sda7 Swap
UUID=83c0bbf6-8c94-480e-8c12-17b6788940ad   none                 swap     sw                                                               0  0  
```

I recommend using the UUID's instead of /dev/sdX as I have had sda #'s change on me. I had a # of 10GB partition in my extended when I installed Windows to /dev/sda4 (My extended was sda3), and when I rebooted into Ubuntu, they were all renumbered (sda4 became sda3, then everything in the extended which was now sda4 became sequential, as you can see that is no longer the case)

Thank you! This was very helpful. 
I have an external hard drive which I am going to back up all my files with when I get around to carrying out this whole process. Hopefully it will work the first time. If not, then I have no problem with re-installing the operating system and then doing the whole thing with a clean drive. I just really need to dual boot.

> **larrypg said:**
> Hello,

Although I have limited knowledge I think I can see a few problems (and a few questions) if you wanted to install Win 7 to the unallocated space.  Most of the problems associated with this have already been mentioned but it is sort of hard to see exactly how your HD is set up with the thing in the middle.  

If you notice the size of your unallocated space you will see that it is just a tiny slice of the drive.  If you want to also run Win 7 and programs then you need to allocate more of the drive to it. 

Although it is a bit hard to tell exactly, right now you seem to have a 454 Gib / partition which is probably about 10 times bigger than it needs to be.  I am thinking that if you want to run Win 7 and programs you will need around 60 Gib for it. 



This part is where my limited knowledge comes in... I think, although I am not sure, that Win 7 sort of likes to be at the start of the disc.  You would have to move everything to the right to make an unallocated space at the beginning of the disc which can cause a few problems.   

This is just a question but I thought that an extended partition was just a vessel to put logical partitions in but there seems to be a boot flag on the extended itself.  

I sure hope you either have a backup in place or you do not mind erasing the drive but it seems that it would be easier to first install Win 7 and then install Ubuntu. Depending on which you will be using more will determine the amount of space you give it.  

I have a bit more to say but just previewed the post and I am sure long winded.

Yeah, I'm going to re-size the unallocated space to about 100GB for my windows partition.

---

### Post by oscarivera9 on 2011-12-20
> I sure hope you either have a backup in place or you do not mind erasing  the drive but it seems that it would be easier to first install Win 7  and then install Ubuntu. Depending on which you will be using more will  determine the amount of space you give it.  I completely agree that it would be best to simply make a backup of your current Ubuntu setup, then do a fresh install of Windows 7 at the beginning of the hard drive.  Windows likes to be first on a hard drive and I believe it [SIZE=2]_**needs**_[/SIZE] to be on a primary partition.  After installing Windows 7, then you can go ahead and install Ubuntu either on a primary partition (like you have it now), or put it in a logical partition within an extended partition (which is the way I have it).

My system looks something like this:
Windows 7 (primary partition) then the following on logical partitions within an extended partition: 
       Ubuntu 11.10  - -  Mandriva 2011

 I installed the 3 operating systems in this order: Windows, Ubuntu, Mandriva and I had no problems at all with Windows or Ubuntu.  I ran into a slight problem with Mandriva upon initial installation but it was something very minor and I already had expected it prior to installation.
I hope it all goes well for you, and remember that we are all here to help you along the way.

---

### Post by xyzzyman on 2011-12-20
Windows just needs to be in the first NTFS partition and primary. When it's not the first NTFS that's when you run into problems. If there's say for example ext4 or reiser beforehand then it's fine as they are ignored.

---

### Post by AaronDaycentChild on 2011-12-23
> **oscarivera9 said:**
> I completely agree that it would be best to simply make a backup of your current Ubuntu setup, then do a fresh install of Windows 7 at the beginning of the hard drive.  Windows likes to be first on a hard drive and I believe it [SIZE=2]_**needs**_[/SIZE] to be on a primary partition.  After installing Windows 7, then you can go ahead and install Ubuntu either on a primary partition (like you have it now), or put it in a logical partition within an extended partition (which is the way I have it).

My system looks something like this:
Windows 7 (primary partition) then the following on logical partitions within an extended partition: 
       Ubuntu 11.10  - -  Mandriva 2011

 I installed the 3 operating systems in this order: Windows, Ubuntu, Mandriva and I had no problems at all with Windows or Ubuntu.  I ran into a slight problem with Mandriva upon initial installation but it was something very minor and I already had expected it prior to installation.
I hope it all goes well for you, and remember that we are all here to help you along the way.

Thanks man, I appreciate your help. I think I'm going to go about it using this method.

If I do a fresh install and choose the option to "Run Windows Alongside Ubuntu" that should eliminate most of the problems I should be presented with if I just do it the other way.

> **xyzzyman said:**
> Windows just needs to be in the first NTFS partition and primary. When it's not the first NTFS that's when you run into problems. If there's say for example ext4 or reiser beforehand then it's fine as they are ignored.

Thank you! I'll remember that.

---

### Post by oscarivera9 on 2011-12-24
I'm glad I was able to help you in some way.

---

### Post by xyzzyman on 2011-12-26
For future reference to anyone who may come across this thread, while Windows is fine with being on a 2nd or 3rd partition as long as it's the first NTFS, TrueCrypt works much better if Windows is on first partition and you want to multi-boot off one drive with Linux & Grub.

---

