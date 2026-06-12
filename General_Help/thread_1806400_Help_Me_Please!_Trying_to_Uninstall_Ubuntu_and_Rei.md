---
title: "Help Me Please! Trying to Uninstall Ubuntu and Reinstall Windows 7!"
date: 2011-07-17
forum: General Help
---

### Post by theunit8 on 2011-07-17
Hey guys whats up! I'm having a big time problem here and i'm stuck. I know one of you will probably figure it out...somehow.. Well anyways, I installed Ubuntu a while ago, then I just updated to Ubuntu 11.04..Anyways my parents got me Windows 7 for my birthday so I'd like to uninstall Ubuntu and have Windows 7 instead. I'm not a newbie when it comes to this stuff, I'm not great, but i'm also not in the dark with computers. Well I wanted to install Windows 7 so I inserted the disk and booted from the disk drive, anyways I ended up getting an Code 5 message Unable to boot the cd/dvd... something like that, but i'm positive it did say CODE 5...So i'm stuck because I can't boot from the BIOS and I already know I can't boot the disk setup logged on to Ubuntu so I don't know what to do!! I'd like to just wip my computer out and install Windows 7! Can anyone help me?

---

### Post by szal on 2011-07-17
Hmmmm&#8230; 1. Insert Win7 DVD in DVD drive. 2. Boot from DVD. 3. Let the Win7 installer handle the partitioning. 4. Install. 5. Enjoy. &#8212; Don&#8217;t see any procedural problem with that.

As for your &#8220;Code 5&#8221; error, some more information would be helpful: 1. error message as exact as possible; 2. hardware specs (especially BIOS brand and version and DVD drive in use).

Also this is most definitely not a *buntu problem but hardware-related, so it should belong in the Hardware subsection, if not even outside this forum&#8212;poke a mod to move the thread over if it can be fit somewhere here. :)

---

### Post by sirspazzolot on 2011-07-17
When the error message pops up, take a photo and post it here. It'll probably be blurry but it could still help if we could read some of it. "We" meaning the forum, I personally am too dumb to help.

---

### Post by rickytikki on 2011-07-17
> **theunit8 said:**
> Hey guys whats up! I'm having a big time problem here and i'm stuck. I know one of you will probably figure it out...somehow.. Well anyways, I installed Ubuntu a while ago, then I just updated to Ubuntu 11.04..Anyways my parents got me Windows 7 for my birthday so I'd like to uninstall Ubuntu and have Windows 7 instead. I'm not a newbie when it comes to this stuff, I'm not great, but i'm also not in the dark with computers. Well I wanted to install Windows 7 so I inserted the disk and booted from the disk drive, anyways I ended up getting an Code 5 message Unable to boot the cd/dvd... something like that, but i'm positive it did say CODE 5...So i'm stuck because I can't boot from the BIOS and I already know I can't boot the disk setup logged on to Ubuntu so I don't know what to do!! I'd like to just wip my computer out and install Windows 7! Can anyone help me?

well the way you do it is you either set it in your bios to boot from cd first or press f12 after the bios ur computer might be diff so check. After you install win7 your grub loader will be wiped youll need a live cd to fix or rienstall the grub loader so you can dual boot.

---

### Post by theunit8 on 2011-07-17
> **szal said:**
> Hmmmm… 1. Insert Win7 DVD in DVD drive. 2. Boot from DVD. 3. Let the Win7 installer handle the partitioning. 4. Install. 5. Enjoy. — Don’t see any procedural problem with that.

As for your “Code 5” error, some more information would be helpful: 1. error message as exact as possible; 2. hardware specs (especially BIOS brand and version and DVD drive in use).

Also this is most definitely not a *buntu problem but hardware-related, so it should belong in the Hardware subsection, if not even outside this forum—poke a mod to move the thread over if it can be fit somewhere here. :)

I can't do that in Ubuntu though. If I open the Win7 setup, it doesn't run,because Ubuntu doesn't run the Windows files.

---

### Post by ajgreeny on 2011-07-17
I believe your problem is that if you still have only ubuntu on your system, windows is not clever enough to see the linux partitions, and therefore does not know you have a hard disk to install to.

If you want to add windows to your ubuntu and dual boot you, will need to shrink your ubuntu partitions and make some free space, or make a new ntfs partition first, to which you should be able to install windows.  You will then need to run a live ubuntu CD to restore grub and allow dual booting.

---

### Post by theunit8 on 2011-07-17
Here are my screen-shots if this helps whatsoever....

The disk is obviously working
[IMG]http://img88.imageshack.us/img88/4045/33106930.png[/IMG]

Then I click the Disk on the Desktop
[IMG]http://img21.imageshack.us/img21/5881/89980763.png[/IMG]

Then I clicked the Win7 setup exe then of course this happen
[IMG]http://img810.imageshack.us/img810/7633/18626452.png[/IMG]

So that shows that I can not Install Windows 7 inside of Ubuntu right now.. If there's another way you guys know please be very specific!!!
And the other way is starting up the computer and booting the disk drive so the cd/dvd loads first. Well, I did that and a message comes up sayin "Code 5 : Unable to Read CD/DVD" So I can't boot and install. I'm stuck here please help me out guys and girls! I'll try to comply with everything you guys are saying. Again my goal is to just run Windows 7!!!

---

### Post by idoitprone on 2011-07-17
> **theunit8 said:**
> Here are my screen-shots if this helps whatsoever....

The disk is obviously working
[IMG]http://img88.imageshack.us/img88/4045/33106930.png[/IMG]

Then I click the Disk on the Desktop
[IMG]http://img21.imageshack.us/img21/5881/89980763.png[/IMG]

Then I clicked the Win7 setup exe then of course this happen
[IMG]http://img810.imageshack.us/img810/7633/18626452.png[/IMG]

So that shows that I can not Install Windows 7 inside of Ubuntu right now.. If there's another way you guys know please be very specific!!!
And the other way is starting up the computer and booting the disk drive so the cd/dvd loads first. Well, I did that and a message comes up sayin &quot;Code 5 : Unable to Read CD/DVD&quot; So I can't boot and install. I'm stuck here please help me out guys and girls! I'll try to comply with everything you guys are saying. Again my goal is to just run Windows 7!!!

 ok that is not how you install windows. You will have to go to the bios and change the boot order. If you manage to do that then windows will install. You cannot override ubuntu while it is booted. Unless you install windows 7 in a virtual enviroment.

---

### Post by ManualSparrow on 2011-07-17
The OP says he tried to boot from the disk and got an error. 
@OP: You should try booting the Windows7 DVD again. Right when the computer starts press whatever key the BIOS tells you to press for the boot menu, then select your disk drive and post the exact content of that "CODE 5" error you described (if it happens again). You cannot install Windows from within Ubuntu.

I don't think the disk not booting has anything to do with the hard drive, but a few things would be good to know, like:
How you installed Ubuntu in the first place: Did you overwrite the original OS or what? It could be that the MBR (Master Boot Record, typical Windows partitioning scheme) is not being recognized by Windows for some reason, so it thinks that you don't have a target for installation. I would think the Windows 7 install disk would be able to install to any hard drive (if you were willing to wipe it) but I am not sure. Is this disk meant for upgrades only or is it a full installation?

---

### Post by walt.smith1960 on 2011-07-17
Ubuntu and Win 7 can coexist.  You'll have to do what other advise:  Figure out how to boot the CD before the hard drive.  There may be a key like F12 or you may have to change the boot order in your BIOS.  After you install Windows 7, you can then boot from a Ubuntu LiveCD, partition your hard drive so part of it has Windows 7 on it and part has Ubuntu.  I use a boot manager which works well but it isn't necessary, just convenient and adds capability.

---

### Post by Blasphemist on 2011-07-17
Is your optical disk drive a cd drive and not a dvd drive by any chance? If the Windows 7 disc is a new genuine windows 7 disc, it almost surely a dvd. It's also possible that your optical drive is just dirty. You may be able to clean it with a qtip.

Did you get any part of the windows install before the error? If not, do write down the exact error and it may be familiar to us or a google search of the error may tell what it is.

---

### Post by Dangertux on 2011-07-17
Error Code 5 generally means that the media could not be booted. 

Reasons for this include but are not limited to. 

-DVD ROM  drive in safe mode , locked, or DMA is disabled. 
- DMA disabled for hard drive 
- Windows installation media is scratched, damaged or inproperly created

I doubt it is because windows can not "see" the partitions. While Windows can not create an ext file system or read it. It can see , and delete the partitions. Additionally it would be a different error code further along in the process. 

Check your installation media is not damaged, make sure DMA is enabled in your BIOS. If that fails test the media in a known working machine. If that doesn't work I would suggest returning it and trying to get a new disk, should be able to do this through Microsoft (be prepared to provide your license key)

---

### Post by Gremlinzzz on 2011-07-17
check this out
[http://www.unawave.de/windows-7-tipps/code5-error.html?lang=EN](http://www.unawave.de/windows-7-tipps/code5-error.html?lang=EN)

---

### Post by mxyzptlk on 2011-07-17
> **theunit8 said:**
> Hey guys whats up! I'm having a big time problem here and i'm stuck. I know one of you will probably figure it out...somehow.. Well anyways, I installed Ubuntu a while ago, then I just updated to Ubuntu 11.04..Anyways my parents got me Windows 7 for my birthday so I'd like to uninstall Ubuntu and have Windows 7 instead. I'm not a newbie when it comes to this stuff, I'm not great, but i'm also not in the dark with computers. Well I wanted to install Windows 7 so I inserted the disk and booted from the disk drive, anyways I ended up getting an Code 5 message Unable to boot the cd/dvd... something like that, but i'm positive it did say CODE 5...So i'm stuck because I can't boot from the BIOS and I already know I can't boot the disk setup logged on to Ubuntu so I don't know what to do!! I'd like to just wip my computer out and install Windows 7! Can anyone help me?

quick solution:

in ubuntu go to system configuration
disk tools

from your existing partition of ubuntu it should be ext4 create a new one (you have to shrink your ubuntu partition size) ntfs type

since as it was mentioned before windows is dumb (quite a lot) to recognize other type of partitions it wil recognize ntfs as t is yout hdd size

restart your computer hit del(supr) or f12 to choose your boot option and select cd/dvd

your win 7 loader should recognize ntfs partion as your hard disk size and install it

once you have set your disk sector (it doesnt matter where it is) as windows native during the partition and installation of win 7 you are good to go

you can have both operating systems if you choose this option once you have finished installing windows go back o ubuntu and update grub it will recognize windows loader

if you just want win7 once it is installed, run ubuntu from live cd, erease your ubuntu partition with it and that´s it

it works, I have several os in my computer such as ubuntu 11, debian, backtrack and win 7 all of them run perfect

---

