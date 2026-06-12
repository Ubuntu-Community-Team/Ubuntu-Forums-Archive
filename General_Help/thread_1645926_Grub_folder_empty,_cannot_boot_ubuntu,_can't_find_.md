---
title: "Grub folder empty, cannot boot ubuntu, can't find root.disk"
date: 2010-12-15
forum: General Help
---

### Post by TheShoemaker on 2010-12-15
I installed ubuntu 10.10 yesterday. I went through installed and restarted my computer, then shut it down. I turn it back on, select Ubuntu. It boots up for a moment, then displays that it cannot find root.disk. Also, when I go back into windows, it shows my grub folder as being empty. Ubuntu is installed on drive G, not C. So is there something I should/ can do to fix this?
Yes, I had hidden files and folders enabled.
I'm fairly technical literate, but most of my work is website design, so ubuntu is new to me completely. 
P.S. An additional question; is it possible to triple boot a vista system? I was considering also getting red hat linux.

---

### Post by cipherboy_loc on 2010-12-15
How can you "see" your Ubuntu disk from Windows? You should download another .iso, check the MD5 sum, and get ready for some poster (I forgot what his name is) who wanders around with a grub boot info script. I shall see if I can find that link. Anyways, download it on the live cd, make it executable, and post back with the output of it.

** Edit: Here is the link: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)   I think I will add it to my signature...

Cipherboy

P.S. I don't mean any disrespect towards the guy with the boot info script. I will try and remember your username this time... :popcorn:

---

### Post by Hippytaff on 2010-12-15
> some poster (I forgot what his name is) who wanders around with a grub boot info script
 
We are many, I am one ;-)
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
 
also this sounds like a wubi install (installed inside windows rather than next to it), and about the tripleboot, you can boot as many ditros that will fit on you machine :-)

---

### Post by TheShoemaker on 2010-12-15
The actual install is in a folder on my external harddrive called Ubuntu; that's how I can see it.
I have it on a disk and booting it from that disk works fine. The MD5 hash of my .iso is
59d15a16ce90c8ee97fa7c211b7673a8

---

### Post by Hippytaff on 2010-12-15
I think grub needs to be installed on the external HD too, though if you run the boot script from the link I posted and post the results.txt here, people will be able to advise you based on your actual install/setup etc :-)

---

### Post by bcbc on 2010-12-15
> **TheShoemaker said:**
> I installed ubuntu 10.10 yesterday. I went through installed and restarted my computer, then shut it down. I turn it back on, select Ubuntu. It boots up for a moment, then displays that it cannot find root.disk. Also, when I go back into windows, it shows my grub folder as being empty. Ubuntu is installed on drive G, not C. So is there something I should/ can do to fix this?
Yes, I had hidden files and folders enabled.
I'm fairly technical literate, but most of my work is website design, so ubuntu is new to me completely. 
P.S. An additional question; is it possible to triple boot a vista system? I was considering also getting red hat linux.
The grub folder is supposed to be empty. That's not the problem. It's a leftover from the days when grub-legacy was used.

I don't think the Windows installer (Wubi) is ideal for you, especially if you want to triple boot. But if you have some important data or really want to fix this install, then post the bootinfoscript results and we'll try and help out.

---

### Post by cipherboy_loc on 2010-12-15
The md5 sum you posted checks out. I should create a utility that will check if the .ISO is valid... BRB.  ;)


Cipherboy

---

### Post by bcbc on 2010-12-15
> **cipherboy_loc said:**
> The md5 sum you posted checks out. I should create a utility that will check if the .ISO is valid... BRB.  ;)


Cipherboy

Wubi checks the md5sum automatically when you install... (unless you specify --skipmd5check as a command line option)

---

### Post by TheShoemaker on 2010-12-15
Don't you have to run it ("it" being boot_info_script055) from the terminal in ubuntu? I can't even load the OS. It stops and said it couldn't find the aforementioned file, so if I'm right, (I seriously doubt I am) then it won't work. 
Oh, and many thanks to everyone for the assistance so far!

---

### Post by Hippytaff on 2010-12-15
if you do
```

cd Downloads/

``````

./boot_info_script055.sh

```the scripts will do it's thing - I've always found it generates the results.txt file in the folder it was run from, so in this case the Downloads folder. Post that in code tags (go to New Reply, paste the text, highlight it and click the # button above the text window)

Edit -> also check out this post...Wubi fixes by Rubi1200 - [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by TheShoemaker on 2010-12-15
It took me a moment to figure it out what to do, but the file is attached. I booted from the live disk and typed into the terminal ```
sudo bash ~/Downloads/boot_info_script*.sh
```It took me several frustrating minutes to figure out that I had to redownload it so that this would point to a valid location. But I did, and there it is. Attached. I doubt you care about the figuring it out part, but oh well. Another second or so of reading.
I hope the file talks about the WUBI installation, not just the disk.

---

### Post by bcbc on 2010-12-15
There's a little weirdness with sda4 - it looks like the partition table is a bit messed as it says sda1 overlaps sda4.

Where and what is 'drive G:'. From what I can see, there's drive C: - your sda3 and that's it. Did you install to an external drive?
If you installed to a USB drive, make sure it's plugged in and turned on when you boot.

---

### Post by TheShoemaker on 2010-12-15
I installed it to a 594 (yeah, I know, odd amount to make a drive) GB external hard drive. That's what volume G is. And yeah, there are a million things installed on G that link to C and vice versa; mainly through shortcuts.

---

### Post by bcbc on 2010-12-15
When you ran the bootinfoscript, the external drive was not switched on. If Ubuntu doesn't boot when the external is plugged in and on, then please run the bootinfoscript again with it on so I can see what's there. (There's no issue running Ubuntu off an external in this way - I've done it many times).

---

### Post by TheShoemaker on 2010-12-15
The external drive is always plugged in, and automatically comes on when the computer does. Should I boot into Ubuntu from the disk, and then unplug and replug the external so it "finds" it or something? Because I don't recall seeing it in Ubuntu's pseudo version of my computer.
The drive is Toshiba and its formatted NTFS (I figured I wouldn't need a FAT32 volume).

---

### Post by bcbc on 2010-12-15
ntfs is fine - it's preferred over fat32 as fat32 has a 4GB file size limit. 
It looks like Windows is mounting the external whenever you boot, but your bios isn't. Which is a problem because the wubi ubuntu install doesn't boot via Windows (just the windows installer part). So, unless you can somehow get your bios to mount the drive when it starts up, then it's not going to work for Wubi.

---

### Post by TheShoemaker on 2010-12-15
Ok. Yeah, I was reaching a similar conclusion. I'm going to go into bios and see what I can do.

---

### Post by TheShoemaker on 2010-12-15
I went into my bios. I placed my HDD above everything but the cd-rom. And, as a result, my computer didn't load anything but an error message telling me just that. Now, I reverted it (I think I put it a step below where it was supposed to be) and Ubuntu's install can't be found at all; much less attempt to start. That wasn't my best idea ever. 
I think I am just not supposed to have Ubuntu. Then again, I can just blame Microsoft and their incompatibility with everything else.

---

### Post by bcbc on 2010-12-15
> **TheShoemaker said:**
> I went into my bios. I placed my HDD above everything but the cd-rom. And, as a result, my computer didn't load anything but an error message telling me just that. Now, I reverted it (I think I put it a step below where it was supposed to be) and Ubuntu's install can't be found at all; much less attempt to start. That wasn't my best idea ever. 
I think I am just not supposed to have Ubuntu. Then again, I can just blame Microsoft and their incompatibility with everything else.
You don't want the external usb to boot prior to your hard drive (as there is no bootloader on it). So maybe the fact that nothing booted means it does see the usb. 

But it doesn't explain why it wasn't included in the bootinfoscript or why Wubi isn't booting. What type of computer do you have? Some bios'es have a USB setting - legacy or something - try flipping whatever it's set to now and see if that makes a difference. (That's just a wild stab).

---

### Post by TheShoemaker on 2010-12-16
My computer is an Inspiron-1501. I've upgraded it heavily, bit it's still slow. 
Anyways, I tried the bios. There wasn't any setting like that.

---

### Post by TheShoemaker on 2010-12-16
I think I may have something. See, now I get the following error.
I get the dual boot screen, I click on Ubuntu, and I get this.
Windows failed to start. A recent hardware or software change might be the cause.
To fix the problem:
1. Insert your Windows installation disc and restart the computer.
2. Choose your language settings and click next.
3. Click "repair your computer"

If you do not have this disc, contact your system administrator or computer manufacturer for assistance.

File: Ubuntu\winboot\wubildr.mbr
 
Status: 0xc000000e
 
Info: The selected entry could not be loaded because the application is missing or corrupt.

See, the thing is, that file is actually just in C:\wubildr.mbr
I think I'll use easyBCD or something and see if it works.

---

### Post by TheShoemaker on 2010-12-16
I'm at  the main screen (the first one when you open the application). 

```
There are a total of 2 entries listed in the bootloader.

Default: Windows Vista (TM) Home Basic (recovered) 
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows Vista (TM) Home Basic (recovered) 
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {0af8d286-c31c-11dd-8793-e558f23cc042}
Drive: G:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr

```But, like before, it says that wubildr should be in that spot. The error in boot says the location is on C, this thing says G. Wubildr is there on the G:\ drive. That location points to it, but it doesn't load from there, it chooses the "C" location. Should I create a folder on C with that location and put it there? I think I will and I'll see what happens.

---

### Post by cipherboy_loc on 2010-12-16
> **TheShoemaker said:**
> I'm at  the main screen (the first one when you open the application). 

```
There are a total of 2 entries listed in the bootloader.

Default: Windows Vista (TM) Home Basic (recovered) 
Timeout: 10 seconds
EasyBCD Boot Device: C:\

Entry #1
Name: Windows Vista (TM) Home Basic (recovered) 
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe

Entry #2
Name: Ubuntu
BCD ID: {0af8d286-c31c-11dd-8793-e558f23cc042}
Drive: G:\
Bootloader Path: \ubuntu\winboot\wubildr.mbr

```But, like before, it says that wubildr should be in that spot, not where it actually is. So should I shift it to that spot?

Sure; make a backup of the file and copy it to the correct location from the LiveCD. 

Cipherboy

---

### Post by TheShoemaker on 2010-12-16
And now we're back at the beginning. It makes it, but fails to find root.disk. The problem, I think, is that it is looking for it all in C when it needs to do that in G.

---

### Post by bcbc on 2010-12-16
Whatever you change the entry to, won't help if the g: drive isn't mounted at boot time. And playing with it will only put your windows install at risk - so don't.

Try and shovel some data around, make space on C: and reinstall there. Or partition your local disk drive and install there. 

Whatever you do take backups.

---

### Post by TheShoemaker on 2010-12-16
Yeah, I'll try that. But making the space won't be easy. I only have nine GBs open, and I want more than 1 spare GB. Alright, I'll post back when I've done it.

---

### Post by TheShoemaker on 2010-12-16
It didn't work. It can't find sbd3, or root.disk.

---

