---
title: "Windows 7 slow after Ubuntu 10.10?"
date: 2010-11-27
forum: General Help
---

### Post by ephexeve on 2010-11-27
I had windows 7 on a HDD of 1,5TB, so I installed Ubuntu 10.10 (Dual boot), I made a 300GB partition for it. Then I bought a new HDD of 80 GB, so I deleted Ubuntu from the partition I made, and then extended for Windows, so then I had 1,5TB for Windows and Ubuntu on a 80GB installed.
I have 3 HDD on my computer. One for files another for Windows and another for Ubuntu.
I used Ubuntu till today, then I booted on Windows, I noticed Windows is being way to slow now, it's crashing a lot (And Ubuntu is being a little bit slow too, could be faster).
Here are my computer detail:

[B]4GB DDR3
3 HDD (640(Files),1,5(C: ),80(Ubuntu))
AMD x3 445 3.10GHZ
Windows 32Bit (Patched for 4GB+)
Ubuntu 32Bit
ATI Radeon 4670[/B]

Any ideas why? Before I had Ubuntu on my new HD installed, everything worked fine/great/perfect. But after I installed Ubuntu on a new HDD, Windows is crashing a lot and etc.
I only use Windows for Photoshop and etc. I am a Linux beginner, I haven't manage how to install Photoshop there yet. :(
Any help out there?
(***Btw, I am new to this forum, so hello all :D)***
Thanks

---

### Post by squenson on 2010-11-27
I would first remove the 80 GB disk and see whether Windows is back to a normal speed. Let us know!

---

### Post by ephexeve on 2010-11-28
@[squenson]("http://ubuntuforums.org/member.php?u=481986"),
I tried and I got a grub error in the start-up. Black screen saying grub not found, I had the chance to write something, but I don't know where to start.
Thanks

---

### Post by squenson on 2010-11-28
OK, re-plug the disk and start Windows. There may be references into the registry to the hard drive where Ubuntu is. Launch RegEdit (I am not sure it is the same under Windows 7...) and do a search of the hard drive letter used by your Ubuntu disk. Changes the references to another drive/path that exists, on the Windows HDD.

---

### Post by ephexeve on 2010-11-28
@squenson,

I tried that too, didn't work either.
I just reinstalled EVERYTHING.
I formated everything using Windows. Then installed Windows 7 (Using right now), and I can pretty much tell you, it totally sucks, very slow, crashes a lot, long boot. 
I haven't installed Ubuntu yet, I was thinking to format everything again, using a bootable HD partition CD and format/clean/try to fix everything again, what do you say ?
What I REALLY would love to do, it install only Ubuntu and thats it, nothing else, no other system, but my CPU coller is way to noisy, and on Ubuntu, I havent found any program to change the fan speed, and at Windows I did (FanSpeedController), and I need some tools too, like Photoshop and etc. (I have the ISO on my computer) but I haven't manage to install it in Ubuntu, really have no idea how, wine didn't work either.
Help?
Thanks

---

### Post by squenson on 2010-11-28
Another idea: are your three HDDs properly configured between masters and slaves? Modern HDDs usually don't have such manual settings but older HDDs -- and my guess is that your 80 GB one is in this category -- have small jumpers that should be properly set.

After removing the 80 GB HDD, I would re-install Windows 7 and see if everything is back to normal. Could it be a hardware issue?

---

### Post by ephexeve on 2010-11-28
They are all Sata's..So there is no master/slave =(

---

### Post by ephexeve on 2010-11-29
So, I installed windows about 3 times now, and still very slow.
I already ground 0 formated and nothing =(
I checked for error in both HDD and nothing
Anyone?
Thanks

---

### Post by squenson on 2010-11-29
Well, it seems it is a Windows 7 problem or a hardware problem and it has nothing to do with Ubuntu. I suggest you post your concerns on a Windows forum, there is not much we can do here!

---

### Post by ephexeve on 2010-11-29
Yeah, true, I just had a BlueScreen. I think I know what it is.. Could it be My IEEE 1394 Bus Host controllers?
I have one and I checked at Computer management and it has the yellow sigh and it says:

"Your computer's system firmware does not include enough information to properly configure and use this device.  To use this device, contact your computer manufacturer to obtain a firmware or BIOS update. (Code 35)"
(And if I try to update, it says the best driver is already installed..)
Could it be? Maybe?

---

### Post by tha-mee on 2010-12-01
Photoshop doesn't run in ubuntu for as far as I know (That's the reason I still have a vista partition)

---

### Post by Mark Phelps on 2010-12-01
You would better going to sevenforums.com --  a Win7 forum.  They have forums for diagnostics and can help you figure out why Win7 is performing so badly.

---

### Post by srikanth.gundaz on 2010-12-02
See, your system has 3HDD's and that too with 1.5TB of HDD. So its really not possible for the system to handle all 3devices. Better partition 50gb of drive in 1.5TB HDD and install Ubuntu and disconnect your 80GB HDD. U will have no problems here after.
After disconnecting 80GB HDD, if u get grub or any sort of msg's starting with GRUB, then put your windows 7 CD and boot with that CD. When first screen comes, select Repair your computer. Now you will be shown terminal.
Here type, > fixboot
fixmbr
Now you can login to windows as before. Freshly install Ubuntu in 50gb drive and you can see the change :)   Your system will be as fine as before :)

---

### Post by Mark Phelps on 2010-12-02
> **srikanth.gundaz said:**
> See, your system has 3HDD's and that too with 1.5TB of HDD. So its really not possible for the system to handle all 3devices. 
WHAT?? I have a Win7 system with 7 drives (including 2 1.5TB drives) and it handles them just fine!

> if u get grub or any sort of msg's starting with GRUB, then put your windows 7 CD and boot with that CD. When first screen comes, ...
They're NOT having problems with Win7 booting -- they're having problems with it running slowly.  Restoring the boot loader files and the MBR will have NOTHING whatsoever to do with that!

Read the post before you offer advice.

---

### Post by srikanth.gundaz on 2010-12-02
> **Mark Phelps said:**
> WHAT?? I have a Win7 system with 7 drives (including 2 1.5TB drives) and it handles them just fine!


They're NOT having problems with Win7 booting -- they're having problems with it running slowly.  Restoring the boot loader files and the MBR will have NOTHING whatsoever to do with that!

Read the post before you offer advice.

Hello boss. I am not posting anything unrelated things here. 
> I would first remove the 80 GB disk and see whether Windows is back to a normal speed. Let us know!
@squenson,
I tried and I got a grub error in the start-up. Black screen saying grub not found, I had the chance to write something, but I don't know where to start.
Here, someone had posted about this. So i gave him option of > fixboot
fixmbr

Moreover, there is no effect on Windows if we do something for Ubuntu. Both are completely different. Ubuntu has  NOTHING whatsoever to do with Windows. So, if his system is running slow, then its the problem with 3HDD's. Incompatibility issues. So, if he removes 80GB HDD and try, i am pretty sure that his problem will be solved :)

---

### Post by ephexeve on 2011-01-30
I found out what problem I had, it was my 1.5 HDD, it was corrupted. Thanks for your help guys. Btw, when I get this black screen with Grub not found, what am I suppose to do? is there anyway to get Ubuntu back? or do I need to reinstall everything back ?

Cheers

---

### Post by Mark Phelps on 2011-01-31
> **ephexeve said:**
> I found out what problem I had, it was my 1.5 HDD, it was corrupted. 
So, it had nothing whatsoever to do with the NUMBER of drives connected, right?

A corrupted or failing drive will cause repeated read & write attempts -- slowing ANY machine to a crawl.

Good thing you found out what it was.
>  Btw, when I get this black screen with Grub not found, what am I suppose to do? is there anyway to get Ubuntu back? or do I need to reinstall everything back ?


If it was on your corrupted 1.5TB drive, I doubt that it's salvageable -- since that drive was having such severe problems.

If you have a new drive, you could try the following:
1) Download Clonezilla Live and burn it to CD (you can get it from distrowatch.com)
2) Boot a PC from that CD, with both the new drive and old drive attached.
3) Use CloneZilla to clone the old drive to the new drive
4) Try booting from the new drive.

My guess is that the old drive is so corrupted that even if the cloning works, the new drive won't boot -- but it's worth a shot.

---

### Post by ephexeve on 2011-02-01
Yes, clone my HD, that is a good idea, I shall do that.

But everything is working fine now, I bought I new HDD, so the 1.5 I am using for data.
But when I said before, when I tried to turn my computer on, (fourth post or something) I had a grub error, and I had the chance to write something, in case that happens again, what do I need to write?

---

### Post by bilallucky on 2011-02-01
I got a grub error in the start-up. Black screen saying grub not found,  I had the chance to write something, but I don't know where to start.

---

### Post by ephexeve on 2011-02-01
Exactly, what would be the code to restore grub? Do I need to write something there? Or do I need to reinstall everything back?

---

### Post by Mark Phelps on 2011-02-01
> **bilallucky said:**
> I got a grub error in the start-up. Black screen saying grub not found,  I had the chance to write something, but I don't know where to start.

You can start by NOT hijacking this thread.  We're trying to help the OP solve their problem -- we don't need you jumping in with yours.

Please start your own thread.  That way, we can focus on your problems separately.

---

### Post by Mark Phelps on 2011-02-01
> **ephexeve said:**
> Exactly, what would be the code to restore grub? Do I need to write something there? Or do I need to reinstall everything back?

If you have a multi-drive situation (multiple physical hard drives) and one of them is devoted MS Windows, my recommendation is NOT to write GRUB to that drive. Instead, use GRUB on the other Ubuntu drive(s) and boot using them.  Then, after you're in Ubuntu, open a terminal and enter "sudo update-grub".  This will regenerate the GRUB menu and add an entry for MS Windows.

This keeps your MS Windows drive MBR intact, and also keeps it bootable on its own -- making it a LOT easier to do repairs if needed.

---

### Post by oldfred on 2011-02-01
the sudo update-grub updates the grub menu with all found systems, but does not reinstall grub. I always want the boot loader of a system on the same drive as the system and set BIOS to boot grub2 as it lets me boot all systems.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can also reinstall the windows boot loader to the windows drive with a windows repair CD or install lilo which works just like the windows boot loader. Windows or lilo in the MBR just look for the boot flag and jump to that partition to continue booting. Change sda if not drive sda.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

