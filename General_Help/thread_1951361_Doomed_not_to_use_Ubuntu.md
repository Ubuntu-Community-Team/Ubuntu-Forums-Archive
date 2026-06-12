---
title: "Doomed not to use Ubuntu?"
date: 2012-04-02
forum: General Help
---

### Post by paranoiid on 2012-04-02
I've tried so many times to get Ubuntu running side by side with my Windows 7 but every time something just falls flat on it's knees. This time I decided to try the wubi-thing. It all worked fine, I rebooted and was met by HDI0_GET_IDENTITY_FAILED: or something like that.

Problems from before leads me to believe this is a problem with gnome2(?) doesn't really understand that I run a RAID0. 

I have 3 partitions on a 1x2Tb, one for the system (C: in Windows) one for the programs/games and one for downloads/misc. I tried installing wubi using the C: partition and it wouldn't bite.

I've tried to read, google but it's a jungle. I get more and more confused by each answer and that none seems to have this particular problem.

Now am I doomed to never be able to dual-boot Ubuntu or is there some relatively simple solution to this?

Any answers are appreciated.

---

### Post by 0011235813 on 2012-04-02
> **paranoiid said:**
> I've tried so many times to get Ubuntu running side by side with my Windows 7 but every time something just falls flat on it's knees. This time I decided to try the wubi-thing. It all worked fine, I rebooted and was met by HDI0_GET_IDENTITY_FAILED: or something like that.

Problems from before leads me to believe this is a problem with gnome2(?) doesn't really understand that I run a RAID0. 

I have 3 partitions on a 1x2Tb, one for the system (C: in Windows) one for the programs/games and one for downloads/misc. I tried installing wubi using the C: partition and it wouldn't bite.

I've tried to read, google but it's a jungle. I get more and more confused by each answer and that none seems to have this particular problem.

Now am I doomed to never be able to dual-boot Ubuntu or is there some relatively simple solution to this?

Any answers are appreciated.

OK you're confusing me. You say you have RAID0? Yet you also say you have a **1x2TB** drive! RAID by definition means you have two or more identical drives, otherwise it is not called RAID. 

What you seem to be describing is multiple partitions, in which case find a suitable partition manager program in Windows, make a fourth partition, format it (ideally ext4, though NTFS will do fine) and in the wubi installer, select the fourth partition as the installation drive. 

Hope that helped.

---

### Post by paranoiid on 2012-04-02
> **0011235813 said:**
> OK you're confusing me. You say you have RAID0? Yet you also say you have a **1x2TB** drive! RAID by definition means you have two or more identical drives, otherwise it is not called RAID. 

What you seem to be describing is multiple partitions, in which case find a suitable partition manager program in Windows, make a fourth partition, format it (ideally ext4, though NTFS will do fine) and in the wubi installer, select the fourth partition as the installation drive. 

Hope that helped.

Sorry for the confusion, a bit of a typo. 2x1TB ie two 1TB drives in RAID0.

---

### Post by QIII on 2012-04-02
I can't help you with Wubi.

However, if you want to dual boot the alternate install disk is required for RAID configurations.

---

### Post by imachavel on 2012-04-02
what did you say your error was again? A grub error? can you get into one partition? If so, download boot repair disk .iso:

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

burn it via .iso burner whether it be .iso magic or brasero burner, your choice, and you have two options:

1) run the boot repair, it will fix any file system mbr or grub in master boot sector. I recently fixed two windows partitions, one being windows 7, the other being windows 8, when a fresh windows 8 install messed up grub

2) if that doesn't work, create a boot info script, and compress it, then upload it here to the Ubuntu web server as an attachment in a reply

that will help address the issue

raid 0 instead of 1? So you are going for faster boot time instead of reliability? Don't forget your cpu kernel processor calls are the core of your pc, if that bottlenecks, it doesn't matter how fast your front side bus, how much ram, how many rpm cycles your disk drives are doing, nothing can get past the processor. None the less if you configured raid correctly, don't forget it works like this, it is writing to both disks at once, so if you have two partitions, then it is more like this:

disk 1: partition 1, partition 2

disk 2: partition 1, partition 2

I am assuming you are using a Sata raid configuration instead of two Ide drives, in which you need one to be master, and the other to be, well slave? Either way while installing each OS, by pressing f6 it will configure that for you in bios, but the jumper settings on each hard drive need to be set correctly.

Can you give us more info about the issue? What exactly is going on when you boot up the pc? Did you at one time have access to two partitions, I must admit, I could be wrong, but:

WUBI install + raid set up? Sounds like a recipe for disaster. I would have used gparted to boot to after installing the first OS with raid, and created a brand new partition. WUBI and raid just does not sound like they agree much :confused:
I never did understand from forum admins correctly, how does WUBI install a new partition if one file system is already mounted? Well it sounds like something you could easily do from disk management

to OP: network connectivity, drivers all working well for one partition? Otherwise it will be hard to upload the boot info script. Can you ping ubuntu.com? Getting a good connection with your i.s.p. dns server?

---

### Post by imachavel on 2012-04-02
> **QIII said:**
> I can't help you with Wubi.

However, if you want to dual boot the alternate install disk is required for RAID configurations.

which alternate disk?

---

### Post by QIII on 2012-04-02
The alternate installer disk from Ubuntu.

---

### Post by imachavel on 2012-04-02
right, with raid in case during install it doesn't ask for raid install option with f6?

[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)

I gotta ask less questions, and google more. Thanks though

---

### Post by paranoiid on 2012-04-02
> **QIII said:**
> I can't help you with Wubi.

However, if you want to dual boot the alternate install disk is required for RAID configurations.

I've tried that and it resulted with Windows 7 not showing in the boot menu (even after a grub2 update) and various other things. I believe i took me a weekend to get it to show and after that Ubuntu just wasn't itself anymore.

So is there any guide for dummies to do that? Or just some helpful tips? 


> **imachavel said:**
> what did you say your error was again? A grub error? can you get into one partition? If so, download boot repair disk .iso:

[http://sourceforge.net/projects/boot-repair-cd/](http://sourceforge.net/projects/boot-repair-cd/)

burn it via .iso burner whether it be .iso magic or brasero burner, your choice, and you have two options:

1) run the boot repair, it will fix any file system mbr or grub in master boot sector. I recently fixed two windows partitions, one being windows 7, the other being windows 8, when a fresh windows 8 install messed up grub

2) if that doesn't work, create a boot info script, and compress it, then upload it here to the Ubuntu web server as an attachment in a reply

that will help address the issue

raid 0 instead of 1? So you are going for faster boot time instead of reliability? Don't forget your cpu kernel processor calls are the core of your pc, if that bottlenecks, it doesn't matter how fast your front side bus, how much ram, how many rpm cycles your disk drives are doing, nothing can get past the processor. None the less if you configured raid correctly, don't forget it works like this, it is writing to both disks at once, so if you have two partitions, then it is more like this:

disk 1: partition 1, partition 2

disk 2: partition 1, partition 2

I am assuming you are using a Sata raid configuration instead of two Ide drives, in which you need one to be master, and the other to be, well slave? Either way while installing each OS, by pressing f6 it will configure that for you in bios, but the jumper settings on each hard drive need to be set correctly.

Can you give us more info about the issue? What exactly is going on when you boot up the pc? Did you at one time have access to two partitions, I must admit, I could be wrong, but:

WUBI install + raid set up? Sounds like a recipe for disaster. I would have used gparted to boot to after installing the first OS with raid, and created a brand new partition. WUBI and raid just does not sound like they agree much :confused:
I never did understand from forum admins correctly, how does WUBI install a new partition if one file system is already mounted? Well it sounds like something you could easily do from disk management

to OP: network connectivity, drivers all working well for one partition? Otherwise it will be hard to upload the boot info script. Can you ping ubuntu.com? Getting a good connection with your i.s.p. dns server?

I knew it would be a recipe for disaster yet I pressed on, with vigilant faith for the developers. My faith failed me. 

Everything works well, on a 100/100Mbps line with DMZ configured on the machine.

*On the issue: *After the install it asks me to reboot, which I do. It tries to automatically boot into Ubuntu (ignoring the boot list) to which I'm greeted with the error previously stated. It says something about missing an sdc drive? And logs me into one of those fail-safe-terminal-thingies that seem to punch me every time I type something into it.

Then I reboot and I come to the boot list, both Windows 7 and Ubuntu is listed, Windows 7 boots just fine, Ubuntu does the same thing.

I wouldn't call me a computer novice at all, in fact I'd called myself a very advanced computer user yet every Linux distribution has kicked my *** every single time.

---

### Post by Needicla on 2012-04-02
> **paranoiid said:**
> I've tried so many times to get Ubuntu running side by side with my Windows 7 but every time something just falls flat on it's knees. This time I decided to try the wubi-thing. It all worked fine, I rebooted and was met by HDI0_GET_IDENTITY_FAILED: or something like that.

Problems from before leads me to believe this is a problem with gnome2(?) doesn't really understand that I run a RAID0. 

I have 3 partitions on a 1x2Tb, one for the system (C: in Windows) one for the programs/games and one for downloads/misc. I tried installing wubi using the C: partition and it wouldn't bite.

I've tried to read, google but it's a jungle. I get more and more confused by each answer and that none seems to have this particular problem.

Now am I doomed to never be able to dual-boot Ubuntu or is there some relatively simple solution to this?

Any answers are appreciated.


I have Windows 7, I'm facing the same problem but worse.

---

### Post by paranoiid on 2012-04-04
Halp. :(

---

### Post by mastablasta on 2012-04-04
> **paranoiid said:**
>  
I wouldn't call me a computer novice at all, in fact I'd called myself a very advanced computer user yet every Linux distribution has kicked my *** every single time.
 
 
maybe that would be because you are trying to stick another operating system with it :-D try only linux on the disk array.
 
anyway, can you tell what the problem is now as your post sounds a bit like you've managed to solve your issue.

---

### Post by paranoiid on 2012-04-04
> **mastablasta said:**
> maybe that would be because you are trying to stick another operating system with it :-D try only linux on the disk array.
 
anyway, can you tell what the problem is now as your post sounds a bit like you've managed to solve your issue.

But I still want to play teh gamez that Wine really doesn't like sometimes! 

I'm still having the same trouble; how do I dual-boot Ubuntu considering my RAID configuration (software, chipset-based) and that I still want to be able to boot into Windows.

---

### Post by paranoiid on 2012-04-14
Last time I'll bump. I promise.

---

