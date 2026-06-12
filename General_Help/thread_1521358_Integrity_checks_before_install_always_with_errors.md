---
title: "Integrity checks before install always with errors! (Impossible to install)"
date: 2010-06-30
forum: General Help
---

### Post by Locobox on 2010-06-30
Hi, everyone

I've tried to install Linux Ubuntu 9 on an HPmini 110, since this type of netbook doesnt have any optical unit (CD/DVD Reader) I decided to install Ubuntu from an USB flash drive, I created the booteable USB drive with Lili USB Creator, then when I reboot the HPMini and select the "check integrity" option before install, it's always the same error, when the check is finished it tells me "Encountered 1 error in 1 file" (With no description of this error whatsoever) even when Lili USB Creator previously did a succesfull integrity check of the same ISO I'm trying to install. 

I'have installed this same version of linux before (on the same machine), from the same ISO image without this error, I also have tried with 3 different flash drives and lately even tried downloading again the ISO image of Ubuntu 10, I dont think is my hardware either since Ive tried to install this same image in 2 different laptops 1HPmini and 1 HPCompaq CQ60 with the same results at the integrity test.

Any help on this matter would be highly appreciated !!!

/Marc

---

### Post by bobcollard on 2010-06-30
> **Locobox said:**
> Hi, everyone

I've tried to install Linux Ubuntu 9 on an HPmini 110, since this type of netbook doesnt have any optical unit (CD/DVD Reader) I decided to install Ubuntu from an USB flash drive, I created the booteable USB drive with Lili USB Creator, then when I reboot the HPMini and select the "check integrity" option before install, it's always the same error, when the check is finished it tells me "Encountered 1 error in 1 file" (With no description of this error whatsoever) even when Lili USB Creator previously did a succesfull integrity check of the same ISO I'm trying to install. 

I'have installed this same version of linux before (on the same machine), from the same ISO image without this error, I also have tried with 3 different flash drives and lately even tried downloading again the ISO image of Ubuntu 10, I dont think is my hardware either since Ive tried to install this same image in 2 different laptops 1HPmini and 1 HPCompaq CQ60 with the same results at the integrity test.

Any help on this matter would be highly appreciated !!!

/Marc
Instead of an integrity check try the md5sum for the iso.  If it checks out then use it.  You could have a bad file or  bit in that flash drive other than the iso.

---

### Post by uRock on 2010-06-30
Which version are you trying to install? 9.04 or 9.10? 

Also, are you using the Desktop or the Netbook edition?

It may be even easier to install using [Unetbootin]("http://unetbootin.sourceforge.net/").

I also recommend using Ubuntu 10.04LTS.

---

### Post by Locobox on 2010-06-30
Hi, Thanks for the quick reply!

@bobcollard
I've heard of MD5 checks but never try it before, any tutorial or lead on this matter?
I also suspect from the flash drives (1 I think) but 3 of them with data errors??? 

@uRock
I'm using 9.10 desktop version, but also tried 10 LST of ubuntu with same results, going to give it a try to [Unetbootin]("http://unetbootin.sourceforge.net/") looks interesting!

Thanks again guys!

---

### Post by bobcollard on 2010-06-30
> **Locobox said:**
> Hi, Thanks for the quick reply!

@bobcollard
I've heard of MD5 checks but never try it before, any tutorial or lead on this matter?
I also suspect from the flash drives (1 I think) but 3 of them with data errors??? 

@uRock
I'm using 9.10 desktop version, but also tried 10 LST of ubuntu with same results, going to give it a try to [Unetbootin]("http://unetbootin.sourceforge.net/") looks interesting!

Thanks again guys!
Try this for md5sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by warfacegod on 2010-06-30
+1 to uRock for suggesting unetbootin.

Also keep in mind that some jump drives tolerate being used as an installer better than others. For example, I have a 4 GB PNY Attache that I can no longer use an installer. I got about half a dozen different installers onto it and it quit. I can still use it as a regular jump drive but it is no longer recognized as a bootable device by any computer I've tried it on. Now, on the hand, I have a 4 GB Gigaware that has seen better than 50 different installers and is still going strong.

---

### Post by Locobox on 2010-07-01
Thanks Bobcollard for the link on MD5!

Hi warfacegod, in my case I've installed Linux Ubuntu 9 before from the same USB flash drive I'm having trouble with, as I mentioned before I've also tried to do this with 3 different flash drives with the same problem (using Lili USB Creator for the USB task).

I put the ubuntu 10 ISO into another USB flash drive using unetbootin as suggested, everthing went fine but with unetbootin, before the installation I've no way to check for the integrity of the installer, I just selected default and let the installation start, it installed and when the computer rebooted after the GRUB screen lots of DOS-like messages with all sorts of errors appeared!!! even when Ubuntu 10 loaded after those errors, I know this is not normal.

Any idea???

---

### Post by uRock on 2010-07-01
I think the errors you are seeing are not supposed to be seen. They are supposed to be hidden by the splash screens(the purple ones) I think those errors are the OS searching for different hardwares. As long as it doesn't lock up it is fine.

How is the system running for you otherwise?

---

### Post by Locobox on 2010-07-01
It do locks up at start up and sometimes I get to the OS, remmember that this is the very same machine Ubuntu used to installed side by side with windows.

I think I'm going to try a "frugal" installation, someone told me about this kind of install method for computers with no DVD drive or USB port.

I'll see what I can do...

Thanks for the response!

---

### Post by warfacegod on 2010-07-01
I'd test the HDD. I know you said you'd tried on different machines and with different jump drives. Still, testing the drive is a good idea.

---

### Post by Locobox on 2010-07-01
Already done that with HDD Tune Pro (in windows) with no errors encountered on both machines!

What could it be??? I really need Ubuntu installed on this machine!

/Marc

---

### Post by warfacegod on 2010-07-01
We've pretty much gone over everything that is a likely cause.

Have you been messing with the BIOS?

Have you tried installing without ACPI?

Can you install older versions of Ubuntu?

Have you tried any other Distros?

Have you tried the Live Environment to see if that works?

Is the HDD formatted using a file system that Linux can install to, such as ext3 or 4?

---

### Post by Locobox on 2010-07-02
I know its also strange to me, I've installed Linux before and never encountered this error o any other errors, it used to be a painless process...

I 've not changed anything on the BIOS apart from the USB configuration for first booteable device!

I tried to install ubuntu 10, when the integrity check failed I tried installing v9 with the same result: "1 error in 1 file" (no description of the error or file). Besides those 2 versions on Ubuntu I havent tried with any other distro.

Live Environment loads and seems to be ok (no hang ups or errors) but  how can I be sure it is running fine apart from having the GUI loaded???

I let the ubuntu installer to manage the kind of partition format it needs, I only select to install ubuntu side by side with windows, and after the installation I can see from windows that the partition used by Ubuntu is not FAT or Fat32.

What are you refering to by installing without ACPI?


Thanks for your time helping me on this!
/Marc

---

### Post by warfacegod on 2010-07-02
Boot into LiveUSB and then press F6 and select acpi=off.

I have no idea when you are supposed to hit F6 for a Lucid disc. I imagine it would be on the screen that asks you if you want to install or try Ubuntu, like it is on 9.10 and back.

If this doesn't work then I'm out of ideas. Except to suggest trying to install another distro to see if it will install properly.

Glad to help.

---

### Post by warfacegod on 2010-07-02
Actually I take that back. I have another idea. Even better two.

One. I just say this again:

> Already done that with HDD Tune Pro (in windows) with no errors encountered on both machines!

For all intents and purposes, Windows is totally incapable of reading Linux ext4. That's the filesystem that Ubuntu now defaults as, for installing. It's possible that there *is* a flaw and Windows simply can't see it. Boot into a Live Environment and do:

```
sudo apt-get install gsmartcontrol
```

and then do an Extended Test (this can take some hours so have something else to do). After that do a Conveyance test. If your drive passes *those* then it would be safe to say that this isn't a failing HDD.

Curses! I spent too long typing that up. Now I can't remember my other idea. Fragging hell!

Anyway, you might want to post a screenshot of Gparted. Please do it as an attachment, embedded screenshots can be major hassle to read. Often times, they're either too small to read the text or way too big.

---

### Post by Locobox on 2010-07-04
The test of the HDD for any possible damage done with HDD Tune Pro was done before the other part of the disk were linux formatted.

The MD5 check is OK for the ubuntu 10 installer, so now I know the downloaded ISO is OK. I just cant get linux installed from USB!!!




**What I have tried so far:**

-Downloading the ISO of Ubuntu 10, 3 different times (2 times on windows and 1 on Linux).

-Puting the ISO on 3 different flash drives (All of them positive for that 1 error in 1 file error).

-Tried to USB install linux ubuntu 10 on 3 different PCs (1 Laptop HpCQ60, 1Desktop Intel P4 HT 3.06GHz, 1 HP mini 110 with no DVD-Rom) after the integrity check all of them were positive for the same error.

-Tried to install from an SD card with the same error!

-Also tested all USB drives on the HPMini110, all ports tested OK.






I think I'll have to buy the external USB DVD-Drive for the HPmini so I can install it from a DVD that passed the integrity check. 

Warfacegod, I put that line (sudo apt-get install gsmartcontrol) in terminal but all I got is: -Couldnt find package gsmartcontrol-



What else can I do to get Ubuntu on this machine???

Thanks for the responses!!!

---

### Post by bobcollard on 2010-07-04
> **Locobox said:**
> 

Warfacegod, I put that line (sudo apt-get install gsmartcontrol) in terminal but all I got is: -Couldnt find package gsmartcontrol-



What else can I do to get Ubuntu on this machine???

Thanks for the responses!!!
Did you check your System>Software Sources to see if all the boxes are checked for your Repositories?  Maybe you could borrow a USB CD/DVD drive for an hour?

---

### Post by warfacegod on 2010-07-04
> **Locobox said:**
> The test of the HDD for any possible damage done with HDD Tune Pro was done before the other part of the disk were linux formatted.


Warfacegod, I put that line (sudo apt-get install gsmartcontrol) in terminal but all I got is: -Couldnt find package gsmartcontrol-


Considering the first part, I think gsmart would be pointless.

I suppose it's possible, although highly unlikely, that all of your jump drives have damage in the same place.

Go with bobcollard's idea. Better to borrow than buy and find out it won't.

---

### Post by Locobox on 2010-07-05
> **bobcollard said:**
> Did you check your System>Software Sources to see if all the boxes are checked for your Repositories?  Maybe you could borrow a USB CD/DVD drive for an hour?

Hi again!

I just tried to do the install with the External USB DVD-Drive but after the integrity test I got the same error message, notice that this is the same DVD that tested OK (with no errors on a desktop computer) after the error I tried to install it anyway but at 60% of the process I got a dialog box: -"input/output error"- the dialog box also suggested me to try to clean the disc bla, bla ,bla.

I dont know what to do now! a technician tested the USB ports and found nothing wrong!!! I just cant use the USB ports to install linux, other than that everything is OK!

How can I install linux without the use of the USB's??? 

Thanks for your time!

---

### Post by warfacegod on 2010-07-05
There is clearly something wrong hardware wise. What Linux did you have install previously and had you tried to install that one again as a test?

---

### Post by Locobox on 2010-07-05
The linux version that used to be installed on this machine (HPMini) was ubuntu 9.10 and I had no problems at all! same machine, same install method (USB flash drive).

I formated the HDD on the HPmini, with the HDD wiped out the integrity checker didnt find any errors, so it must be the windows partition "The Error", the usb flash drive worked fine without windows on any partition...

I know thats the problem, but why???

---

### Post by warfacegod on 2010-07-05
Correct me if I'm wrong but I'm pretty sure this was the first mention of Windows. Regardless, Have you tried to install 9.10? If it works then do an Upgrade Install if you really want Lucid.

---

### Post by bobcollard on 2010-07-05
> **warfacegod said:**
> Correct me if I'm wrong but I'm pretty sure this was the first mention of Windows. Regardless, Have you tried to install 9.10? If it works then do an Upgrade Install if you really want Lucid.
Bingo, Windows?

---

### Post by Locobox on 2010-07-05
Yes windows is installed on the HPMini, I used to have windows xp and linux installed **side by side** with no problems, then erased ubuntu to make some space onto the XP partition, then formatted the HDD installed xp first and then tried the linux installation like ever, but with errors, I do mention I've windows XP installed on this machine on comment #9:


> **Locobox said:**
> It do locks up at start up and sometimes I get to the OS, remmember that this is the very same machine Ubuntu used to installed side by side with windows.

I think I'm going to try a "frugal" installation, someone told me about this kind of install method for computers with no DVD drive or USB port.

I'll see what I can do...

Thanks for the response!

---

### Post by bobcollard on 2010-07-05
I thought you had erased the Windows because you said "Ubuntu used to installed side by side with windows."  I believe your problem is in the Formatted drive, NTSF.

---

### Post by Locobox on 2010-07-05
> **bobcollard said:**
> I thought you had erased the Windows because you said "Ubuntu used to installed side by side with windows."  I believe your problem is in the Formatted drive, NTSF.

Probably a little vague my initial description of the problem... anyway... yes, as I said windows XP is installed on the same 250GBs hdd, and I have installed before ubuntu 9.10 succesfully on this same HDD with no errors! (via USB).

The 250GBs HDD has 2 partitions: 1 for WinXP (NTFS formatted) 150GBs and another unallocated (100Gbs non formatted) partition reserved for linux. Is the same setup I used to install ubuntu before.

...

Hope that helps!

---

### Post by warfacegod on 2010-07-05
Post a screenshot of Gparted from the LiveCD. I think the problem is that you're trying to install into unformatted space. Perhaps you installed as Wubi last time and that's why the first Linux worked.

---

### Post by Locobox on 2010-07-05
> **warfacegod said:**
> Post a screenshot of Gparted from the LiveCD. I think the problem is that you're trying to install into unformatted space. Perhaps you installed as Wubi last time and that's why the first Linux worked.


Thanks for the advice... as you can see I'm not and advanced Linux user, I know what Gparted is but dont know what Wubi is, I dont even know if my installer has wubi (not that I have seen that tool or option)...

I'll post the gparted screen cap...

---

### Post by Locobox on 2010-07-15
I gave up, I cannot install Linux side by side with windows on this machine!!!

Here is a photo of the screen you asked, hope this makes sense:

[http://www.locobox.org/thumbs/hpmini110_cap.JPG](http://www.locobox.org/thumbs/hpmini110_cap.JPG)

One more doubt...

Is it possible to move a windows installation to a partition within a linux HDD, I mean I got Linux properly installed on another HDD on this laptop HP Mini 110 (Hdd 160Gbs) this HDD is partitioned, I want to "move" or migrate Windows to the second partition on this HDD so I dont have to install it (windows) all over again (which means some 4 days with all the apps I use), is it possible???

Thanks for the help

---

### Post by warfacegod on 2010-07-16
It's *theoretically* possible but in practice you'll most likely break windows doing it.

Looking at your screenshot gives me a thought. Have you tried "Specify Partitions Manually" and told it to use another partition other than Windows?

You'll have to forgive me if you already answered that but I've been busy for over a week. Sorry.

---

### Post by Locobox on 2010-07-16
Sure, I hve tried to set Partitions Manually within the Linux setup screen, same results as ever, lots of errors after installation!

The only problem seems to be windows xp installed on the HDD (I know it sounds kinda like a bad joke!...but thats how it is!) I want to put linux on, on the same hdd without windows there's no errors, so it is not the installer, the usb port, or the computer it is something with the partition table but cant be sure bout that either.

As for the windows xp migration to the "new" linux HDD I think I'll open a new thread to see what can I do about.

It's so frustrating this used to be a click and go routine!!! whats happening now??

Thanks for the help warfacegod!

---

### Post by warfacegod on 2010-07-16
Sure thing. Sorry it didn't work out for you.

---

### Post by Locobox on 2010-07-19
Installed succesfully Linux ubuntu 9.10 in the problematic machine (HP Mini 110)


After a lot of "forum" reading, I followed the advice of one user who suggested to install linux on the same HDD from another PC!


He never said if this worked before, but I decided to try it, so I took the HDD from the HPmini to a desktop pc and ran an integrity check, before installation, which finished with NO errors at all, then I proceed to install linux... everything went fine and when the installation finished I removed the HDD from the "host" desktop pc and loaded the HDD into the HPmini, linux booted ok but halted after some DOS-like screen that told me something about some inconsistencies between the machine and the HDD (which is normal considering that linux was installed on this HDD from another computer).

This DOS-Like screen gave me the option to fix this automatically and then asked for reboot, when the machine rebooted everything was OK with no errors, I'm updating the system right now with no problems.

So that was it! it seems to be some sort of problem with the USB ports on the HPmin110 dont know for sure (I use all the 3 USBs with no problems, the only problem I encountered was when trying to install linux thru USB!!!)

So far so good, but is there any routine checks to asure that the system is indeed healthy??? Somewhere to look when problems appear in linux??? (like Device manager 
on windows)???

Thank you all for the help!

---

### Post by warfacegod on 2010-07-19
Open a Terminal:

```
sudo apt-get install gnome-device-manager
```

I can't remember if it will tell you hardware status or not but it's the only thing I can think of.

---

### Post by Locobox on 2010-07-19
Thanks warfacegod, going to give it a try!

---

