---
title: "restoring RAID 0"
date: 2012-05-29
forum: General Help
---

### Post by sputtle on 2012-05-29
It killed my RAID 0 AGAIN! This is not a HDD failure problem

2 years ago i thought I would give Ubuntu a try since I had heard so much hype about it. Once it was installed, the RAID 0 set up was gone.. Again, this is not a HDD failure problem.

Here I am again, trying a different approach. I installed Ubuntu on a 16 gig flash drive. Once I restarted and booted ubuntu from the flash drive, I was playing around with it, saw it worked, restarted again to go back into windows.. Both HDDs were working just fine, but once Ubuntu touched my computer, it killed the RAID again.. WHY?! WHY I ASK DOES UBUNTU HAVE TO SUCK SO BADLY!!!! Once again, this is not a HDD failure problem

Does anyone know a fix for this? I have not installed any software, my HDDs should be fully intact, I just need the metadata rewritten, or the RAID to be restored. I already checked the BIOS and the settings haven't changed. The mobo is still set up for RAID. And just to be sure, one last time, this is NOT an HDD failure problem!

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> It killed my RAID 0 AGAIN! This is not a HDD failure problem

2 years ago i thought I would give Ubuntu a try since I had heard so much hype about it. Once it was installed, the RAID 0 set up was gone.. Again, this is not a HDD failure problem.

Here I am again, trying a different approach. I installed Ubuntu on a 16 gig flash drive. Once I restarted and booted ubuntu from the flash drive, I was playing around with it, saw it worked, restarted again to go back into windows.. Both HDDs were working just fine, but once Ubuntu touched my computer, it killed the RAID again.. WHY?! WHY I ASK DOES UBUNTU HAVE TO SUCK SO BADLY!!!! Once again, this is not a HDD failure problem

Does anyone know a fix for this? I have not installed any software, my HDDs should be fully intact, I just need the metadata rewritten, or the RAID to be restored. I already checked the BIOS and the settings haven't changed. The mobo is still set up for RAID. And just to be sure, one last time, this is NOT an HDD failure problem!

Some machines have problems with Ubuntu. I had a lot with graphic cards. You just have to find out what is causing the problems, which can admittedly be somewhat wearying, but there is no point in saying that something sucks just because you can't get it to work as you would like it to.

When I have a problem with Ubuntu, I invariably assume that I have screwed up somewhere, and try to find out where. This has proven to be an excellent policy. Sometimes some software or other may be "at fault", but mostly it is something I have done, or not done, which is causing the problems.

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> Some machines have problems with Ubuntu. I had a lot with graphic cards. You just have to find out what is causing the problems, which can admittedly be somewhat wearying, but there is no point in saying that something sucks just because you can't get it to work as you would like it to.

When I have a problem with Ubuntu, I invariably assume that I have screwed up somewhere, and try to find out where. This has proven to be an excellent policy. Sometimes some software or other may be "at fault", but mostly it is something I have done, or not done, which is causing the problems.
Yes, I do understand that. That is why I didn't get upset at all the first time this happened. But now, I installed this OS on a FLASH DRIVE. Completely separate from my HDDs. Just because the OS is ran it decides to screw up the RAID? That's quite ridiculous. And I'm not the first person with this problem. I've been trying to research fixes and there's no solutions to be found, just a long list of problems.

---

### Post by sputtle on 2012-05-29
WINDOWS software is fully capable of identifying these types of settings and working WITH them. Not against them.. If this is such a common problem, why was I not informed by the OS. I've been working with Windows ever since 3.1 so I already know all the ins and outs and usually don't have to worry about things like this. But I thought I would try something different, like Ubuntu. I heard it was good.. and in my experience it didn't last 5 seconds in the "good" category. I just wish the makers of this OS would think things through, just a little bit. Since they are incapable of doing that. They suck, imo. This isn't version 1, 2 or 3. It's version 12.04. So c'mon devs.. use your brain cuz you just cost me a **** ton of time that's now wasted because of a crappy OS.

---

### Post by gnusci on 2012-05-29
If you want someone here help you, please, just moderate the vocabulary.

---

### Post by gnusci on 2012-05-29
> **sputtle said:**
> WINDOWS software is fully capable of identifying these types of settings and working WITH them. Not against them.. If this is such a common problem, why was I not informed by the OS. I've been working with Windows ever since 3.1 so I already know all the ins and outs and usually don't have to worry about things like this. But I thought I would try something different, like Ubuntu. I heard it was good.. and in my experience it didn't last 5 seconds in the "good" category. I just wish the makers of this OS would think things through, just a little bit.

If you want to talk about another OS, just do it in their forums.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> Yes, I do understand that. That is why I didn't get upset at all the first time this happened. But now, I installed this OS on a FLASH DRIVE. Completely separate from my HDDs. Just because the OS is ran it decides to screw up the RAID? That's quite ridiculous. And I'm not the first person with this problem. I've been trying to research fixes and there's no solutions to be found, just a long list of problems.

There may not be a "simple" fix for your particular problem. That's just how it is.  have you tried installing the raid properly under Ubuntu?  Or is this a raid setup on a machine running another system?

If Ubuntu tries to mount things it doesn't know anything about there may well be problems.

---

### Post by sffvba[e0rt on 2012-05-29
If you only ran Ubuntu and didn't install anything then your RAID should still be 100% intact and not affected.

I would suggest waiting for someone with experience with this to post and assist you.


Regards
404

---

### Post by strask on 2012-05-29
> **sputtle said:**
>  restarted again to go back into windows.. Both HDDs were working just fine, but once Ubuntu touched my computer, it killed the RAID again.
Can you provide more detail on the specific errors you get when you try to boot into windows?

I absolutely trust that you are correct that this is not a drive failure problem, but what messages do you see that indicate that?

The more detail you can provide, the more likely it is that someone will be able to help you.

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> There may not be a "simple" fix for your particular problem. That's just how it is.  have you tried installing the raid properly under Ubuntu?  Or is this a raid setup on a machine running another system?

If Ubuntu tries to mount things it doesn't know anything about there may well be problems.
I was considering that, but I'm afraid to have anything installed on the HDDs. I wanted to keep this OS separate because of the RAID issue. I'm clinging to a hope that all data hasn't been lost yet and there may yet be a recovery option somewhere.

---

### Post by sputtle on 2012-05-29
> **strask said:**
> Can you provide more detail on the specific errors you get when you try to boot into windows?

I absolutely trust that you are correct that this is not a drive failure problem, but what messages do you see that indicate that?

The more detail you can provide, the more likely it is that someone will be able to help you.
I have a gigabyte mobo and use it's built-in raid controller. Just after POST and before the HDD test it will attempt initialization of the RAID. I forget the actual message, I'd have to restart to be exact. But it lists the detected drives and the condition of the RAID on each. In this case there's 2 seagate barracudas. It lists the serial number of them, then on the right side under status, it usually says "online" when working, but now says "Offline". Then once its finished initializing the raid, it verifies the DMI (?) pool data then says "DISK BOOT FAILURE.... something something, i'd have to restart to see the exact message. But it doesn't anything about the master boot record. It just says boot failure in all caps.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> I was considering that, but I'm afraid to have anything installed on the HDDs. I wanted to keep this OS separate because of the RAID issue. I'm clinging to a hope that all data hasn't been lost yet and there may yet be a recovery option somewhere.

If you try to mix systems you are going to have problems. I run a number of machines with Windows and a number with Ubuntu, and I also use some other systems. They all have their advantages, disadvantages and peculiarities.

You can't run a gas powered car on diesel.

If Windows does what you want and you are happy with it, then stick to Windows. There are lots of ways to recover raid data.  Unfortunately, you have not given any pertinent information on that.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> I have a gigabyte mobo and use it's built-in raid controller. Just after POST and before the HDD test it will attempt initialization of the RAID. I forget the actual message, I'd have to restart to be exact. But it lists the detected drives and the condition of the RAID on each. In this case there's 2 seagate barracudas. It lists the serial number of them, then on the right side under status, it usually says "online" when working, but now says "Offline". Then once its finished initializing the raid, it verifies the DMI (?) pool data then says "DISK BOOT FAILURE.... something something, i'd have to restart to see the exact message. But it doesn't anything about the master boot record. It just says boot failure in all caps.

Ubuntu can not boot a disk setup from another system. There is no way to do it.

Is the Ubuntu disk you are using a copy of an installed system?  You can boot a live system using certain utilities, but you can not get a raid setup from another system to boot. It is not possible.

If the Ubuntu system you are using attempts to boot a system which it is not set up to do it will fail every time, it it pointless even trying.

What system have you been using the RAID on?   Windows?  If so, you need to use Windows utilities to recover it.  There are loads to choose from, but this is an Ubuntu forum.

We don't even know what system you were using the raid on. If it was Windows 7 for instance, you will get excellent help here;

[Windows 7 Forums]("http://www.sevenforums.com/")

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> If you try to mix systems you are going to have problems. I run a number of machines with Windows and a number with Ubuntu, and I also use some other systems. They all have their advantages, disadvantages and peculiarities.

You can't run a gas powered car on diesel.

If Windows does what you want and you are happy with it, then stick to Windows. There are lots of ways to recover raid data.  Unfortunately, you have not given any pertinent information on that.
  Hold on a second. Multiboot OS isn't a new thing. It can and is done quite often. If this were a single drive, there would have been no issues in the first place, for me, 2 years ago when I was originally trying to do this.

No, you cannot run a gas powered car on diesel, but you can run a gas powered car on E85, given the right components.  So in the spirit of your analogy, I was attempting to setup my computer, 2 years ago, to be a flex fuel car. And in this case, I was attempting to put together a mobile back-up engine, in case of failure, for friend and family rescue. But the mobile engine cut the gas line..

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> Ubuntu can not boot a disk setup from another system. There is no way to do it.

Is the Ubuntu disk you are using a copy of an installed system?  You can boot a live system using certain utilities, but you can not get a raid setup from another system to boot. It is not possible.

If the Ubuntu system you are using attempts to boot a system which it is not set up to do it will fail every time, it it pointless even trying.

What system have you been using the RAID on?   Windows?  If so, you need to use Windows utilities to recover it.  There are loads to choose from, but this is an Ubuntu forum.
Ubuntu is working just fine, running off of the flash drive now. It is how I am able to be here on this forum. It's Windows that no longer works. It's the 2 HDDs that were in RAID that have the problem. And it's that setup that I would like to recover. But I don't go to the windows forums, because windows didn't do anything wrong. Ubuntu did. Windows users who have no experience with Linux would have no idea how to solve this problem (I'm just addressing an earlier post here of why I'm not posting on another OS's forums.)

Ubuntu is installed on the flash drive as if it is a USB HDD. I used a utility to do this. The ISO was fully unpacked and installed to the flash drive so the HDDs should not have been touched to run the OS. I'm not trying to boot windows from Ubuntu at all. I want windows to boot when the USB is no longer plugged into the system.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> Hold on a second. Multiboot OS isn't a new thing. It can and is done quite often. If this were a single drive, there would have been no issues in the first place, for me, 2 years ago when I was originally trying to do this.

No, you cannot run a gas powered car on diesel, but you can run a gas powered car on E85, given the right components.  So in the spirit of your analogy, I was attempting to setup my computer, 2 years ago, to be a flex fuel car. And in this case, I was attempting to put together a mobile back-up engine, in case of failure, for friend and family rescue. But the mobile engine cut the gas line..

I am not going to argue about it. I was attempting to help you. What you actually do is your own affair.

If you put diesel in a gas powered car, it's your own fault that it doesn't work. It has nothing to do with the fuel or the car.

If you set the RAID up to run under Ubuntu it will work perfectly, as it doubtless now does in whatever system you are using.

If you want Ubuntu to run properly then you have to install it properly.

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> I am not going to argue about it. I was attempting to help you. What you actually do is your own affair.

If you put diesel in a gas powered car, it's your own fault that it doesn't work. It has nothing to do with the fuel or the car.

If you set the RAID up to run under Ubuntu it will work perfectly, as it doubtless now does in whatever system you are using.

If you want Ubuntu to run properly then you have to install it properly.
I'm not trying to argue. Really not. But I am looking for insight on why Ubuntu messed with the RAID in the first place. Actually, I'd be happy with a fix to restore the HDDs the way they were without that information. My biggest point here is, Ubuntu was installed on a flash drive. The whole point was for it to be completely independent from any PCs HDDs. I didn't worry about the RAID setup because it was never intended to be on the RAID, at least this time.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> Ubuntu is working just fine, running off of the flash drive now. It is how I am able to be here on this forum. It's Windows that no longer works. It's the 2 HDDs that were in RAID that have the problem. And it's that setup that I would like to recover. But I don't go to the windows forums, because windows didn't do anything wrong. Ubuntu did. Windows users who have no experience with Linux would have no idea how to solve this problem (I'm just addressing an earlier post here of why I'm not posting on another OS's forums.)

Ubuntu is installed on the flash drive as if it is a USB HDD. I used a utility to do this. The ISO was fully unpacked and installed to the flash drive so the HDDs should not have been touched to run the OS. I'm not trying to boot windows from Ubuntu at all. I want windows to boot when the USB is no longer plugged into the system.


Which Windows are you using? Which utilities did you use to set up the system? is your BIOS set correctly for a default boot?

Neither Windows nor Ubuntu has "done anything wrong", you have.  If you want help to sort out your system then either give some relevant information on the matter or stop wasting people's time.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> I'm not trying to argue. Really not. But I am looking for insight on why Ubuntu messed with the RAID in the first place. Actually, I'd be happy with a fix to restore the HDDs the way they were without that information. My biggest point here is, Ubuntu was installed on a flash drive. The whole point was for it to be completely independent from any PCs HDDs. I didn't worry about the RAID setup because it was never intended to be on the RAID, at least this time.

I am bound to assume that you made some mistake or other when setting up the system. That is invariably the problem with these things. I run several such systems which default to booting something else and have no problems with them. I will try to help you find that mistake if you provide the relevant information.  I am not interested in personal opinions of various operating systems. 

Obviously the Ubuntu system should not be able to touch the existing system. If it does, then you have set it up incorrectly.

I would bet you have the BIOS set incorrectly for what you want to do.

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> Which Windows are you using? Which utilities did you use to set up the system? is your BIOS set correctly for a default boot?

Neither Windows nor Ubuntu has "done anything wrong", you have.  If you want help to sort out your system then either give some relevant information on the matter or stop wasting people's time.
I was running Windows 7

Unetbootin was used to install the software onto a flash drive using this walk-through: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

And as stated in my first post, the BIOS is still set up to run the RAID. In fact, I'm having trouble figuring out how Ubuntu accessed a single drive while the BIOS was in this setting. I'm no expert in this area and it is something I'll have to research further. In the meantime, if anyone has any idea if its possible to restore the hard drives the way they were, and how to do it, I would greatly appreciate the help.

---

### Post by sputtle on 2012-05-29
On second thought, I have no proof that Ubuntu did access a single drive. All I know is once Ubuntu was ran on this machine, the drives themselves were no longer accessible. Whether or not they wrote something to the drive is a bit of a mystery to me, but I know for sure the RAID settings in the BIOS were never changed. It has been a reliable raid every step of the way for over 3 years until I give Ubuntu a try.

---

### Post by sffvba[e0rt on 2012-05-29
When you boot to the Windows system, is the USB with Ubuntu still inserted? Also, when booting Ubuntu, do you get a menu with the possibility to boot Windows?


404

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> On second thought, I have no proof that Ubuntu did access a single drive. All I know is once Ubuntu was ran on this machine, the drives themselves were no longer accessible. Whether or not they wrote something to the drive is a bit of a mystery to me, but I know for sure the RAID settings in the BIOS were never changed. It has been a reliable raid every step of the way for over 3 years until I give Ubuntu a try.

So, you did not set up the BIOS to boot Ubuntu ( The drive you stuck the card or whatever in), and to boot the RAID as the default? If so, that is your problem.

Set your BIOS to boot the drive you have Ubuntu in FIRST, and the RAID next. When Ubuntu is not present the machine will default to booting the RAID.

If you just stick an Ubuntu system into a machine it will try to use whatever is there. You have to set the machine up properly.  I would try to explain how you could do that, but you still have not provided any relevant information which would allow me to do so.

Do you want your machine running again, or do you just want to vent your frustration?

Please decide, and either provide the information or go and vent somewhere else.

---

### Post by sputtle on 2012-05-29
I remove the USB stick when I try to boot from windows completely. Currently the Hard disk priority in the BIOS is 1 USB, 2 Bootable Add-in Cards, 3 Hard Drive. And when I boot from Ubuntu, I get no such choices at all. It loads right into Ubuntu.

---

### Post by sputtle on 2012-05-29
> **traditionalist said:**
> So, you did not set up the BIOS to boot Ubuntu ( The drive you stuck the card or whatever in), and to boot the RAID as the default? If so, that is your problem.

Set your BIOS to boot the drive you have Ubuntu in FIRST, and the RAID next. When Ubuntu is not present the machine will default to booting the RAID.

If you just stick an Ubuntu system into a machine it will try to use whatever is there. You have to set the machine up properly.  I would try to explain how you could do that, but you still have not provided any relevant information which would allow me to do so.

Do you want your machine running again, or do you just want to vent your frustration?

Please decide, and either provide the information or go and vent somewhere else.

I'm not exactly sure what information it is that your looking for. If there's a setting I missed, or something I should change, just say so.

And yes, currently the USB is first boot priority with the HDD set below it.

I actually stay away from bragging about how beast the machine is, especially when for the most part, BIOS settings are alike, and other hardware besides the HDDs and mobo just don't matter. If that's not what your point is, then you've lost me. I'm not sure what you're getting upset about.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> I remove the USB stick when I try to boot from windows completely. Currently the Hard disk priority in the BIOS is 1 USB, 2 Bootable Add-in Cards, 3 Hard Drive. And when I boot from Ubuntu, I get no such choices at all. It loads right into Ubuntu.

There are only limited possibilities here.  Either the BIOS is set up incorrectly or the Ubuntu system  you are using is not suitable for what you want to do.

What Ubuntu are you using? Which utility did you use to make it bootable?

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> I'm not exactly sure what information it is that your looking for. If there's a setting I missed, or something I should change, just say so.

I actually stay away from bragging about how beast the machine is, especially when for the most part, BIOS settings are alike, and other hardware besides the HDDs and mobo just don't matter. If that's not what your point is, then you've lost me. I'm not sure what you're getting upset about.

I am not the least bit upset.  I am attempting to discover the information I need in order to be able to give you sensible advice, which you steadfastly refuse to provide.

Just answer the questions I already asked several times and then I will be able to tell you what is wrong and how to fix it. Everything else is completely irrelevant.

---

### Post by sputtle on 2012-05-29
> **sputtle said:**
> ..... This isn't version 1, 2 or 3. It's version 12.04. So c'mon devs......
> **sputtle said:**
> I was running Windows 7

Unetbootin was used to install the software onto a flash drive using this walk-through: [http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

And as stated in my first post, the BIOS is still set up to run the  RAID. In fact, I'm having trouble figuring out how Ubuntu accessed a  single drive while the BIOS was in this setting. I'm no expert in this  area and it is something I'll have to research further. In the meantime,  if anyone has any idea if its possible to restore the hard drives the  way they were, and how to do it, I would greatly appreciate the  help.  
.

---

### Post by sffvba[e0rt on 2012-05-29
> **sputtle said:**
> I remove the USB stick when I try to boot from windows completely. Currently the Hard disk priority in the BIOS is 1 USB, 2 Bootable Add-in Cards, 3 Hard Drive. And when I boot from Ubuntu, I get no such choices at all. It loads right into Ubuntu.

Typically I would suggest doing the steps listed [here]("http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/") to try and fix your Windows install... I am however not sure if this will work for RAID and also not sure if this will do more damage than good :/

Perhaps someone with more understanding will be along to help.


404

---

### Post by sputtle on 2012-05-29
> **not found said:**
> Typically I would suggest doing the steps listed [here]("http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/") to try and fix your Windows install... I am however not sure if this will work for RAID and also not sure if this will do more damage than good :/

Perhaps someone with more understanding will be along to help.


404
Thank you for looking for a fix for me. This is a fix I will most likely eventually have to do. But the first step is to restore the original RAID settings. As it is right now, the RAID controller reports the drives being "Offline" from the raid despite BIOS settings. I don't know for sure, but I would assume there's a small script of some kind the RAID controller looks for to get read and write settings for the drives. (RAIDS can be set up to write in multiple sized chunks. Going off of memory, I believe mine is set up for 128kb striping.)

So as it is right now, the PC looks at a drive and sees nothing but mumbo jumbo. Its not looking to the 2nd drive to find the missing information. The way RAID 0 or striping works, is it divides all data into equal amounts of 128kb, in my case, onto each drive. So it's only seeing half of the data when looking at a single drive.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> .

You need to fix your RAID under the system you used to set it up. You can follow this tutorial;

[http://www.easeus.com/resource/raid-recovery-software.htm](http://www.easeus.com/resource/raid-recovery-software.htm)

Do not attempt to install anything else to your system.

Then you need to ensure that the Ubuntu system you are using is not set up to install anything.

It is likely that you have the system set to install. That is the only way it could have any effect on your RAID.

There is also quite a bit of freeware available for RAID recovery;

[http://www.dtidata.com/resourcecenter/freeware-data-recovery/](http://www.dtidata.com/resourcecenter/freeware-data-recovery/)

[http://www.sevenforums.com/hardware-devices/153259-data-recovery-raid-auto-rebuild-wrong-hdd.html](http://www.sevenforums.com/hardware-devices/153259-data-recovery-raid-auto-rebuild-wrong-hdd.html)

[http://download.cnet.com/ReclaiMe-Free-RAID-Recovery/3000-2094_4-75289445.html](http://download.cnet.com/ReclaiMe-Free-RAID-Recovery/3000-2094_4-75289445.html)

In order to get the best possible chance of recovering your RAID you need to image the discs using an external bootable CD etc, and then only work on the images. Make a copy of your initial image and try to recover that.  Do not attempt to recover anything directly from the RAID setup.

---

### Post by sputtle on 2012-05-29
Thank you, these look like some useful utilities. I'll have to give them a try.

I hate to ask, but it would be a lot easier....   You wouldn't happen to have found any of these utilities for Ubuntu, have you? Because I don't have a working Windows machine, at the moment.

---

### Post by traditionalist on 2012-05-29
> **sputtle said:**
> Thank you, these look like some useful utilities. I'll have to give them a try.

I hate to ask, but it would be a lot easier....   You wouldn't happen to have found any of these utilities for Ubuntu, have you? Because I don't have a working Windows machine, at the moment.

There are such utilities for Ubuntu, but I am not experienced enough using such utilities with Ubuntu to give you any advice on that.

Somebody else will doubtless be able to help you out.  You could try this; 

[http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Rescue-Remix-34055.shtml](http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/Ubuntu-Rescue-Remix-34055.shtml)

I have it, but have not yet used it.

My main area of expertise is Windows systems, I am basically a "newbie" to Linux.  However, imaging as such is not all that common in the Linux world because there is not much need for it.

You can also use this excellent free software to image your disks;

[http://www.todo-backup.com/business/free-backup.htm](http://www.todo-backup.com/business/free-backup.htm)

You will need to create the boot media ( recovery media) on another Windows machine. It wont run under Ubuntu.  I have done this in a virtual machine quite successfully in the past. But it can become confusing, you are better off with physical devices.

You may in fact be lucky with that, on quite a number of occasions the software has automatically recovered a raid while imaging, or when restoring, but I would not bank on that.

You could set up a virtual Windows machine using this;

[https://www.virtualbox.org/](https://www.virtualbox.org/)  under Ubuntu,

install the Easeus software to the Virtual Machine and burn your recovery media from there. That will work OK.

EDIT:  PS . To avoid all possible problems disconnect your RAID drives from the machine until you have the virtual machine set up and have burned your Windows/Easeus recovery media. Only reconnect them when you have the Easeus bootable Windows recovery media, and remove all Ubuntu systems before proceeding to recover the RAID.

---

### Post by sputtle on 2012-05-30
I have found the fix for this issue and will create a new thread to post it as a solved issue. Hopefully it will be stickied.

---

### Post by traditionalist on 2012-05-30
> **sputtle said:**
> I have found the fix for this issue and will create a new thread to post it as a solved issue. Hopefully it will be stickied.

That's good to hear. I will be most interested. But it is probably better not to fragment threads. Just post here and mark it solved. That way anybody looking for it can find it more easily.

---

### Post by sputtle on 2012-05-30
Oh, my bad.. Unfortunately I already posted it before reading your post. 
 
For anyone reading this thread who has had this problem, the fix is here:
[http://ubuntuforums.org/showthread.php?p=11984216](http://ubuntuforums.org/showthread.php?p=11984216)

---

### Post by traditionalist on 2012-05-30
> **sputtle said:**
> Oh, my bad.. Unfortunately I already posted it before reading your post. 
 
For anyone reading this thread who has had this problem, the fix is here:
[http://ubuntuforums.org/showthread.php?p=11984216](http://ubuntuforums.org/showthread.php?p=11984216)

No problem. Glad to hear you got it fixed.  You should however also check that the Ubuntu system you are using is set up correctly, and that it does not try to install anything when booted.

---

