---
title: "Do i have to format a brand new hd first before installing linux?"
date: 2012-02-28
forum: General Help
---

### Post by fdclemmons on 2012-02-28
I want to use linux as my only OS. Have tried Ubuntu, Fedora and Mepis. All give tons of errors. Does anyone have a real world step by step guide on how to install to a brand new custom built system?  Live CD do not work. Is there a command line option?

---

### Post by grahammechanical on 2012-02-28
You need to get the live CD to work first. What is the problem? Describe the symptoms.

When we install Ubuntu to a blank (new) hard disk the section where we partition the disk or use the entire disk if that is our choice, it is there that we mark the disk to be formatted and we choose the format. The default for the latest Ubuntu is ext4.

I have done this myself with my custom built machine. It is always best to try Ubuntu from a live CD first.

Here is the step by step explanation complete with pictures.

[http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download")

Regards.

---

### Post by elliotn on 2012-02-29
when u install and reach the partitioning part when u check the drive to install to you have to choose ext4 or something Linux compitable then you will have to format to that filesystem.....

---

### Post by hometow1 on 2012-02-29
you can format hd in livecd.

---

### Post by elliotn on 2012-02-29
> **hometow1 said:**
> you can format hd in livecd.

ofcoz he can but also what I meant if when u install ubuntu it will require u to format

---

### Post by fdclemmons on 2012-02-29
I guess my hardware will not work with any version of Linux. So I will reluctantly stick with MicroSuck system. Just pop in the setup media and it takes care of everything. Thank you all for your suggestions.

---

### Post by QIII on 2012-02-29
We'd have helped, if you had given us the symptoms you are encountering.

My first question would have been whether or not you checked the md5sum on the isos you have downloaded and then checked the integrity of the media you burned them to.

Unless your system is somehow significantly different from any other system built from commodity components, I find it hard to believe it will not run Linux.

All of my machines are custom/purpose built.

---

### Post by jocko on 2012-02-29
> **fdclemmons said:**
> I guess my hardware will not work with any version of Linux.
Why don't you describe the problem and see if anyone here know how to fix it?
When you say the live cd does not work, exactly what happens? Are you sure the live cd was burned correctly (it needs to be burned at the slowest possible setting, otherwise you often end up with unreadable sectors)? Have you tried a USB install?

---

### Post by fdclemmons on 2012-02-29
I did post the symptons and the log information showing the errors. You can find my post by searching for "**OEM install problems** " on this forum. I have tried to install from usb, cd, have checked to make sure iso download was correct size, checked the physical CD for errors, burned the iso at 1x speed, ran a surface check on the new hard drive. As I said in my first post "**OEM install problems** ", years ago I installed Redhat Linux on my home computer on the same hard disk as windows 98 with no problem. There were no Live Cd's back then. I had to use four Cd's and use the command line. I have asked if anyone knows if Linux can still be installed via command line, but no one has answered.

---

### Post by jocko on 2012-02-29
> **fdclemmons said:**
>  I have asked if anyone knows if Linux can still be installed via command line, but no one has answered.
You can still use the text based alternate installer. Just get an alternate ubuntu cd from [here]("http://www.ubuntu.com/download/ubuntu/alternative-download#alternate").

---

### Post by jocko on 2012-02-29
> **fdclemmons said:**
> I did post the symptons and the log information showing the errors. You can find my post by searching for "**OEM install problems** " on this forum. ...
The errors you post [there]("http://ubuntuforums.org/showpost.php?p=11714522&postcount=6") clearly indicate that you are trying to install through wubi, but still you claim that you booted the live cd. Perhaps you are a bit confused about what a live session is? Set your bios to boot from the cd first, and start your pc with the cd in the tray. It should immediately boot to the ubuntu live session and NOT start windows.
Wubi is a windows program that installs ubuntu as a file within the windows file system, and even if ubuntu installed this way will run independently from windows you still have to keep the windows partition and boot loader.
If you want a real dual boot you have to use either the live cd installer or the alternate installer, not wubi...

---

### Post by elliotn on 2012-02-29
WUBI is installing ubuntu within Windows thus no partition needed, when ubuntu is installed with WUBI it works as an application in windows.
 
to install Ubuntu in a Hard Drive you need to boot with the liveCD, to do so you need to enter your BIOS and choose first boot with cd/dvd then reboot. BIOS can be entered either using F2 or Del when you hear the first beep

---

### Post by fdclemmons on 2012-02-29
Got Ubuntu to install on the hard drive with windows XP. Now when the system starts I can choose between Ubuntu and XP. When I choose Ubuntu I get Errors. "Kernel Panic" is listed first then other errors.

---

### Post by fdclemmons on 2012-02-29
I inserted the Ubuntu Live CD and chose to install inside WindowsThen the last dialog box showed "Completing The Ubuntu Setup Wizard." Then I had to reboot to complete the installation. After my computer restarted I choose Ubuntu from the boot menu and got the errors I mentioned.

---

### Post by fdclemmons on 2012-02-29
I did set my bios to boot from the cd first, started my pc with the cd in the tray. It  immediately booted to the ubuntu live session, did NOT start windows and gave this error message
"[7.943036] Kernel Panic - not Syncing:VFS:unable to mount root fs on unknown block(8,1)"

I do not have a RAID setup. I have checked every page in the BIOS for a reference to raid to disable it and there is no reference to raid.

---

### Post by QIII on 2012-02-29
Again you said "inside Windows", which several posters recommended against.  Do you want to do a bona fide dual boot or a WUBI install?

Using Wubi Would be counter to your stated purpose, since your machines would still need to have Windows installed.

Don't install inside Windows.  You may be encountering Wubi problems rather than problems with Linux proper.

If you are getting a kernel panic from removable media, then I submit that either the original ISO download is faulty (md5sum does not check) or the ISO has errors from the burn process.

---

### Post by fdclemmons on 2012-02-29
Original ISO download is was not faulty (md5sum does check). The ISO had errors from the burn process. 3 to be exact. I used ImgBurn. Anyone suggest another product. I do have Nero Essentials. Should I be using that instead? In any case I WILL NOT GIVE UP until I get this installed and working properly. I REALLY APPRECIATE ALL OF YOU!!!

---

### Post by QIII on 2012-02-29
Any small fault in either the download or burn process can render your install medium useless.

As for Windows burners I can't say.   Hang tight for someone else.  I'll check in later and see if I can come up with a suggestion if you don't get one.

(BTW, the forum code of conduct says not to badmouth other companies or their products.  I don't use Windows unless I have to -- I have this thing about having food and money for the mortgage.  I have some serious misgivings about the business practices of Microsoft, but most of the world uses Windows and somehow they get along fine.)

---

