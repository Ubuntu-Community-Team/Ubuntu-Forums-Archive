---
title: "A swiss army knife iso"
date: 2010-08-13
forum: General Help
---

### Post by linux18 on 2010-08-13
===========================| Summary |=========================
By combining the lightweight power of debian 5.05 and xubuntu 6.06, I have produced a one of a kind live cd with far fewer system requirements than a standard ubuntu disc. With this technology, it is possible to boot a live cd with xfce desktop environment in just 82 megabytes of ram without swap! With 128 megabytes of ram and a swap file the system will feel about as fast a ubunutu 10.04 live cd with 512 megabytes of ram and a swap file. Right now the ISO is still expirimental, but I forsee it as a great platform for troubleshooting, testing hardware, fixing problems with existing ubuntu installations, and messing with partitions - all while maintaining the 'feel' of ubuntu (including two panels, four workspaces, and the full xfce4 desktop environment). In short, a swiss army knife of tools all packed into an iso smaller than 300MB
-------------------------------------------------------------------------------------------------------------------------

=======================| Inside The ISO  |=====================
Requirements:
Minimum: 82MB of ram and a 133MHz 80486 cpu
Recommended: 96MB of ram and a pentum 2
Best: 128MB of ram and a pentium 4 

Removed from xubuntu 6.06 ISO:
almost everything not required to run the computer

Added to the ISO:
deborphan and the startup configuration 

What's in the ISO:
mousepad, xfarchiver, xfterminal, synaptic,
gparted, network manager, and a few random packages
----------------------------------------------------------------------------------------------------------------

=========================| Whats Next |=========================
I'm looking for suggestions on diagnostic tools and scripts that I shoud include in the nextversion. Please suggest tools to include in your comments. I'm also putting together a customizing script to allow anyone to customize it. 
------------------------------------------------------------------------------------------------------------------

==========================| Download |==========================
The iso comes as a two part .7z file. 
There are two ways to download, script or direct link:
Script:
Links:
[http://download455.mediafire.com/ijldaydp29qg/yo9p9pbe52f2xa9/super-fast.7z.001](http://download455.mediafire.com/ijldaydp29qg/yo9p9pbe52f2xa9/super-fast.7z.001)
[http://download507.mediafire.com/rmc4l033xlfg/hl7bfcsihzy2i5c/super-fast.7z.002](http://download507.mediafire.com/rmc4l033xlfg/hl7bfcsihzy2i5c/super-fast.7z.002)

---

### Post by varunendra on 2010-08-19
Just finished downloading & tried on VMware (512 MB RAM, 2.8GHz C2D- single core in use).

Loading took roughly around 50-58 sec., looks nice!

**A few quick suggestions:**

[LIST]
[*]Web Browser is missing, should be inclueded.
[*]Would be nice if the archiver supports .rar, .7z extensions (seems it is not there yet)
[*]For a 'troubleshooting' live cd, Windows Manager Tweaks seems unnecessary (no prob. if has negligible size & side effect! :))
[/LIST]
**A few issues I had:**

[LIST]
[*]My net conn. is suffering severe problems for almost a month, and such problems are common with Indian ISPs. Had a lot of trouble to download (for the first two days, the page wouldn't open like it was a dead link!). Accordingly, I suggest to kindly include a torrent link if possible.
[*]After downloading, the second part looked like corrupt, I wasted one more day to download it (in fact almost two! yes it's true- 2 days for 119 MB due to continuous breaks causing download-freeze !!). Same again. 7-zip on windows (WinRAR also) failed extracting saying "unsupported compression method for iso". Then I tried p7zip on ubuntu and only then I could extract it successfully. Accordingly I suggest to use original 'One-Piece' iso for torrent, and some standard format for uploads in compressed parts.
[/LIST]
**Suggestion for additional tools:**

[LIST]
[*]I think a rescue/troubleshooting disk is incomplete without TestDisk and PartImage.
[*]Couldn't test but does it have ntfs support?
[*]A decent PDF reader.
[/LIST]

[B]
EDIT:[/B]  Oh.., and 'Quit' doesn't work, 'Power' icon works as log-off (ends xfce session). So had to shut down in two-steps. The 'Quit' option should either be removed or should be made to work as expected.
Overall an appreciable work though! :)

---

### Post by snowpine on 2010-08-19
Interesting concept, thanks for sharing it! A couple of questions before I commit to the download: Does it support ext4 and GRUB2? Those are two must-haves for troubleshooting my current install.

---

### Post by varunendra on 2010-08-19
Hmm.... looks like no to both your questions, I'm not confident though!

man grub returned **grub 0.97**, and gparted didn't show option to format in ext4. Maybe snaps can give a better idea.

---

### Post by linux18 on 2010-08-19
> **snowpine said:**
> Interesting concept, thanks for sharing it! A couple of questions before I commit to the download: Does it support ext4 and GRUB2? Those are two must-haves for troubleshooting my current install.
no etx4 and grub2, the disk is mostly still 6.06 and I didn't wan't to keep the 6.06 packages for ntfs, xfs, jfs, and reiser. 

This first version is essentially to make the ISO as small as possible (ubuntu is a big iso after decompression, which means more memory usage on a live cd) now that I've cut everything out of it, I can start to add packages back into it which include grub2, various filesystem support, and tools for rescuing data off the hard disk.

if anyone can also point to any remianing unnecessary packages or tweaks that can be made, that would also be a big help. I only have a 14KBps upload speed so I wan't real changes before I upload another one.

---

### Post by snowpine on 2010-08-19
> **linux18 said:**
> no etx4 and grub2, the disk is mostly still 6.06 and I didn't wan't to keep the 6.06 packages for ntfs, xfs, jfs, and reiser. 

This first version is essentially to make the ISO as small as possible (ubuntu is a big iso after decompression, which means more memory usage on a live cd) now that I've cut everything out of it, I can start to add packages back into it which include grub2, various filesystem support, and tools for rescuing data off the hard disk.

if anyone can also point to any remianing unnecessary packages or tweaks that can be made, that would also be a big help. I only have a 14KBps upload speed so I wan't real changes before I upload another one.

Fair enough; I will definitely be keeping an eye on the project though. Great idea and good luck with it! :)

---

### Post by DasEi on 2010-08-27
I havent tried it, but looks very nice, though should support ext4 and recent advantages made for other filesystems. An idea to include is :

-blkid
-testdisk
-fsck/e2fsck

---

### Post by linux18 on 2010-08-27
I'm working on the next version and considering eliminating ubuntu 6.06 for a lighter system and chrooting to the ubuntu programs. Thus maximum ubuntu compatibility and minimum overhead.

---

### Post by ventrical on 2010-09-04
Hi linux18,

 I downloaded the file and the zip file will  not open or extract.

It there a download site just for the .iso file?

thanks

---

### Post by linux18 on 2010-09-04
> **ventrical said:**
> Hi linux18,

 I downloaded the file and the zip file will  not open or extract.

It there a download site just for the .iso file?

thanks
It's a .7z file, you can extract it with peazip [http://sourceforge.net/projects/peazip/files/PeaZip%20for%20Linux%2C%20GTK2/3.2.1/peazip_3.2.1.LINUX.GTK2-2_all.deb/download]("http://sourceforge.net/projects/peazip/files/PeaZip%20for%20Linux%2C%20GTK2/3.2.1/peazip_3.2.1.LINUX.GTK2-2_all.deb/download")

It's still an experimental iso and has little in the way of rescue tools.

mediafire has a 200MB upload limit, so a single 250MB ISO is too big to upload

---

### Post by varunendra on 2010-09-04
> **ventrical said:**
> 
 I downloaded the file and the zip file will  not open or extract.

See this....
> **varunendra said:**
> **A few issues I had:**

[LIST]
[*]...........
[*]........ Same again. 7-zip on windows (WinRAR also) failed extracting saying "unsupported compression method for iso". [COLOR=Red]**Then I tried p7zip on ubuntu and only then I could extract it successfully**[/COLOR]......
[/LIST]
 p7zip is in synaptic.

---

### Post by linux18 on 2010-09-04
I'll use regular ZIP for version 2

---

### Post by Dragynn on 2010-09-08
just fyi....

[http://puppylinux.org]("http://puppylinux.org")

The newest distro is called "Lucid Puppy" specifically because it emulates Ubuntu and is able to use their repositories. The entire system runs in ram, it is not even recommended to do a hard install, live is the preferred way to run it. 

The ISO for Lucid Puppy 5.1 is around 130 mb or so, and there are distros that are 70 mb or less for the ISO. The lightest fastest version I found, is TurboPup Xtreme, when loaded onto an old PIII laptop of mine with 512mb of ram, the entire system uses less than 30mb of ram, and yes it does come with a browser already installed. I actually used Lucid Puppy to rescue that laptop, the windoze install was broken and wouldn't boot, it fired right up in Puppy and I was able to save all the old files. Since it all runs in ram and you do a fresh OS load with each boot (and because it's Linux :-)), it's also basically un-hackable and un-virus-able by nature

---

### Post by Dr Watts On on 2010-11-22
Another FYI, I can't imagine a better UTILITY than using the latest pmagic iso (PartedMagic), though Puppy is a verrrry interesting distro. But Puppy is for my playtime, and pmagic is what I use to get work done (emphasis: work... utilitarian tasks, not playing videos etc, tho still could). Since the subject is A Swiss Army knife...:D
DrWattsOn

---

